---
layout: lab
type: lab
date: 2024-02-20
title: 'Individual Project (Project I)'
# pdf: /static_files/assignments/asg.pdf
attachment: /static_files/individual_project_release.zip
# solutions: /static_files/assignments/asg_solutions.pdf
due_event: 
    type: due
    date: 2024-04-06T23:59:59
    description: 'Project I due'
mathjax: true
---
After the previous four labs and several lectures, hopefully you already acquire a general understanding of the IoT data. In this individual project, you will be guided to use the knowledge you have learnt to implement an in-car children presence system. 

## Background

The ability of cars to sense, and save lives, inside a car remains to be improved. One life-critical feature that is widely missing is in-vehicle **Child Presence Detection (CPD)**. Every year, many children have been unintentionally and unknowingly left in parked cars, or have got stuck into a car independently. As the temperature inside a car can rise rapidly, especially in hot months, serious injuries or heatstroke deaths could happen to children being left alone inside a car. It takes only a matter of minutes before the heat can overwhelm a child’s ability to regulate his/her internal temperature and cause injuries/deaths as a child’s core temperatures increase three to ﬁve times faster than an adult’s. On average, around 40 children dying from hot cars have been witnessed each year (about one every 10 days), leading to over 900 pediatric vehicular heatstroke (PVH) deaths on record since 1998 in the US alone. Despite remarkable advances in automobiles in recent years, unfortunately, the cases of hot car deaths are only increasing, with 2018 and 2019 being the record years of 54 and 53 deaths each. All of these deaths could have been prevented, if the car can detect the unattended child timely and responsively alert concerned parties or take prompt actions to keep the car cool and the child safe.

The widespread and tragic problem has driven governments and the auto industry to take initiatives to make CPD a compulsion for future cars, which fosters an expected market of $400 million by 2025. Existing solutions include early systems using special sensors such as optical/weight/pressure/ultrasonic sensors, cameras, as well as recent efforts with Ultra-Wideband (UWB) or millimeter-wave (mmWave) radars, WiFi, etc. These solutions, however, suffer from different limitations. Many works focus on adult passenger monitoring, and cannot generalize well to infants and toddlers. And the sensing coverage is mostly limited to only the seats (for special seat sensors) or a certain Field-of-View (FoV) (for cameras/UWB/mmWave radars), leading to degraded accuracy in Non-Line-Of-Sight (NLOS) scenarios and blind spots, e.g., when a child is in a rear-facing car seat, blocked by a seat, or on the car ﬂoor. More importantly, these techniques require extra hardware that is not standard offerings in today’s cars to be precisely installed. This not only introduces additional hardware and manufacturing costs, which are huge considering more than 80 million new cars annually, but is also backward-incompatible with most of the over one billion existing cars in the world. A truly pervasive system that requires no extra hardware and works for all cars still lacks.

In this project, you will implement an in-cabin monitoring system by using only readily available in-car modules without any hardware modifications. At high level, it operates by transmitting sound signals from the speakers and analyzing their reflections recorded on a microphone, which have interacted with the human body, if present. We present a model, namely **statistical acoustic sensing (SAS)**, to capture the tiny **motions** and extremely weak **breathing** of young children including newborns. 


## Statistical Acoustic Sensing

As you have learnt in the lecture, SAS explores the unseen properties of acoustic multipath reflections, which could be a giant amount. Different from resolving multipath of the acoustic signals, the key insight is, all these multipath distortions, if aggregated properly, can contribute useful information for sensing. Simply put, we calculate the AutoCorrlation (ACF) matrix on the CSI (Channel State Information) of acoustic channel, from which we can acquire motion statistic and breathing rate. 

**You should refer to Lec 5 Wi-Fi Sensing for more details.** Here, the process of SAS is roughly the same as that of Wi-Fi sensing. 

You will be required to implement 4 tasks. First, you are expected to calculate the ACF matrix, based on CSI. This is connected with Lab 3. Afterwards, you have to get the motion over time according to the definition of motion statstic. You will leverage the skills and knowledge acquired from Lab 1-4 to complete the calculation of breathing rate and presence detection.


## Tasks

**You are supposed to implement `individual_project.py`.**

After that, you have to write a report within **ONE** Page with the provided LaTeX template. Missing of report will result in 20% deduction of the grade. **The grading would be based on an comprehensive way, considering both your performance and effort**.

### Working Directory

You should work under `individual_project` directory. The directory tree is:

- \_\_init\_\_.py
- IP_template_comp3516.zip  # Your template of report. 
- check.py
- task_p1.pdf
- report.pdf # You should REPLACE your report
- data/  # store relevant dataset


### Data Format

Normally, we cannot directly acquire CSI from acoustic sensing. For simplicity, we estimated CSI $H(f,t)$ for you. The shape of a given `CSI` is $[N_f, N_t]$, where $N_f$ represents the number of subcarriers and $N_t$ represents total temporal index. The length of one frame CSI (`frame_length`) is 1023 samples.  And the sampling rate for recording is `fs=48000`Hz.

There are two folders under `data/`, `breath` and `presence`, respectively. We will use data under `breath` to evaluate Task P-3 and data under `presence` to evaluate Task P-4. For Task P-1 and P-2, we will use both data. Under each subfolder, there are `train` and `test`. The difference is whether they contain `gt`. The `gt` for `breath` is an integer in BPM, while `gt` for `presence` is `True` / `False`.


### Task P_1: Calculate the ACF matrix (20 points)

**You are required to implement `get_ACF()`**.

Given CSI, you are required to calculate the ACF matrix given window length $w$ and window step $s$. Here we set $w=7$s and $s=0.2$s.

You should return `ACF` matrix, `t_s` in second and `lag` in second. `t_s` represents the time stamp of window. `lag` refers to the time of lag index in ACF graph. The output shape of `ACF` should be `[len(lag), len(t_s), N_f]`.

**Hint:** You need to calculate the CSI sampling rate `Fs`. It is different from acoustic sampling rate `fs`. You should think about how many CSIs (frames) we can acquire per second. 


### Task P_2: Calculate Motion Statistic (20 points)

**You are required to implement `get_ms()`**.

By definition, the motion statistic is given by

$$
g(f, t) = \rho_H(f, t, \tau=1/F_s)
$$
where $F_s$ is the CSI sampling rate. You are required to calculate the motion statistic.  Afterwards, you should average different subcarriers and get
$$
\overline{g(f, t)} = \frac{1}{|F|}\sum_{f \in F} g(f, t).
$$


You should return both $g(f, t)$ `ms` and $\overline{g(f, t)}$ `ms_bar`.

Output Shape:

- `ms`: `(len(t_s), N_f)`
- `ms_bar`: `(len(t_s), )`

### Task P_3: Getting Breathing Rate from ACF (40 points)

**You are required to implement `get_br()`**. You will mainly use the data under `data/breath`.

Now ACF matrix contains different subcarriers for one time slot. Some subcarriers capture dominant breathing signals, while others merely observe noises. Because of the complex multipath propagation, the most sensitive subcarriers can vary over time randomly. Therefore, it is critical to dynamically ﬁnd the best subsets of subcarriers and effectively combine them to maximize the signal SNR.

You are supposed to combine different subcarriers for ACF matrix (for breath detection). Afterwards, you are encouraged to find the combination weight for weighted summation. 

And then, you will detect the **first prominent peak** of ACF matrix to acquire the breathing rate `br` over time. 

Feel free to use filters, if necessary.

**Hint 1:** The key of combination task is to **find appropriate weight**. You have to carefully consider the purpose of enhancing ACF matrix. For example, for ACF matrix, the goal is to enhance the prominence of the first peak while minimizing the significance of subsequent peaks.  You are not required to combine all the subcarriers. Instead, you can apply policies like `topK` subcarriers and optimize the combination of these `K` subcarriers (`K` could be 5-50). The choice of `topK` can be based on the value of $g(f, t)$. You may find MRC in the lecture useful, but that may not be the optimal way. You are encouraged to try different approaches.  You need to clarify the contribution / trials you've made in the report. You may use `find_peaks()` but be careful with the parameters (You can also choose other peak detection / write your own peak detection algorithm as well).

**Hint 2:** Child usually has larger breathing rate than adult. Therefore, in this project, the breathing range would be 12-60 BPM.

You will return the combined ACF, peak index (only the first peak indicating `br`), breathing rate over time, and average breathing rate. The `gt` is the average breathing rate. 

Output shape:

- `combined_acf`: `(len(lag), len(t_s))`
- `peak_index`: `(len(t_s), )`
- `br_t`: `(len(t_s), )`
- `br_mean`: Float 64 number


### Task P_4: Get Presence (20 points)

**You are required to implement `get_presence()`**. You will mainly use the data under `data/presence`.

Now it is time to show your performance of CPD. The presence information can be different across different locations. To simplify your work, we give data in two different environments with label and data in another two environment datas for testing. You can assume simultaneous access to all its data under the same environemt (folder). For example, for `presence/train/env_0`, you can assume you can both see `presence/train/env_0/presence_0.pickle` and `presence/train/env_0/presence_1.pickle`. It is like a one-time calibration.

Please avoid use any conditional handling to iterate over the data (like `if`). We want the `get_presence` to be general. 

You are required to return the presence information. You can use various indicators, including motion and breathing rate. For different dataset, you have to return `True` for presence and `False` for non-presence. 

### Report

You are expected to deliver an **ONE-PAGE report**. We have pre-listed some compulsory points that you have to fill in. You can also add other content, if you think it would be beneficial for your grade. We will depict most of the graphs automatically for you after you run `check.py`. You are welcome to add additional figures which you think can convey your extra contributions. These figures are not included in ONE-PAGE limit, but you'd better have citations to the graph, so that TA can easily navigate. 

You are encouraged to read additional materials / papers and cite them in your report. These references are also excluded from the page limit. (Do not cite course slides / VeCare Paper). A proper reference format will be positive for your grade.

The template is in LaTeX. We recommend you to use [Overleaf](https://www.overleaf.com/) to avoid the hassle of setting up a LaTeX environment. Simply upload the provided zip file to Overleaf to begin your work.

We really want to save your time on formatting, so there should be little cost for you to use LaTeX even if you know nothing previously.

## Submission

**Please run `python check.py --uid <YOUR_UID>` before submitting.** This script performs automated tests on the examples provided in the docstrings. Failing these tests indicates potential critical issues in your code. Strive to resolve these problems. After that, it will create a zip file named after your `uid`. Make sure you enter the right `uid`. 

It's important to avoid changing the names of any files, including both the zip file and the program files contained within. Altering file names can lead to grading errors. Ensure that all file names remain as they are to facilitate accurate assessment of your work.

Your submission to **Moodle** should consist solely of the **generated `*.zip` file**. It is your responsibility to double check whether your submitted zip file includes your latest work. 




