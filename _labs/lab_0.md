---
layout: lab
type: lab
date: 2024-01-22
title: 'Lab #0 Beginning'
# pdf: /static_files/assignments/asg.pdf
attachment: /static_files/lab_0_release.zip
# solutions: /static_files/assignments/asg_solutions.pdf
due_event: 
    type: due
    date: ""
    description: 'Lab #0 due'
mathjax: true
---
Welcome to COMP3516@HKU 2024 Spring. This is an undergraduate elective course for senior CS students. This course focuses on fundamental data analytic techniques applicable to IoT (Internet of Things) data. IoT, a domain centered around ubiquitous sensing and computing, finds its applications in diverse fields such as smart homes, healthcare, edge computing, and security. A key aspect of IoT data analysis is basic signal processing, a skill set that may be new to many of you. Students who have completed ELEC3241 and ELEC3244 will find these concepts somewhat familiar, but prior experience is not a necessity. This course is not structured as a rigorous DSP (Digital Signal Processing) class; hence, intricate mathematical derivations will not be a focal point. Instead, our emphasis will be on using coding to analyze data effectively.

Our course structure includes four lab sessions, each comprising comprehensive tutorials and programming tasks. Lab 1 introduces common IoT signals, while Labs 2 and 3 delve into fundamental signal data analytics, specifically focusing on FFT (Fast Fourier Transform) and ACF (Auto-Correlation Function). In Lab 4, we'll demonstrate techniques to filter out background noise. Post these labs, you'll be well-equipped to analyze IoT data. You are required to implement an individual project, which includes detecting the breathing rate from acoustic data. 

Regarding assessment, the four labs collectively contribute 12 points to your final grade, and the individual project accounts for 10 points.

We are here to guide you through the labs and projects, ensuring you're well-prepared for this exciting journey in IoT data analysis.

## Honour Code

Plagiarism is considered a serious disciplinary offense at HKU. To uphold the highest standards of academic honesty, we will employ advanced software tools to scrutinize submitted code for its originality. Should plagiarism be detected, it will result in significant consequences for all involved parties – both the student who plagiarized and the one who provided the work. The initial penalty for such an offense is a zero score for the implicated assignment. Subsequent offenses will incur more severe disciplinary measures, including potential reporting to the faculty. Rest assured, in such events, you will be afforded an opportunity to present your defense.

Despite these stringent measures, we recognize and support the use of Artificial Intelligence Generated Content (AIGC) tools in your academic work. It is imperative, however, that you clearly acknowledge every instance where AIGC tools have been utilized in your submissions. This transparency is crucial in maintaining the integrity of your work and adhering to our academic standards.

## Environment

The labs are all developed in Python. We recommend you to use `conda` to manage your Python environment, which can be achieved by installing `miniconda` or `Anaconda`. 

We prepare a minimal trial to prepare the environment.

1. Create your environment:
```
conda create --name comp3516 python=3.9
```

2. Enter you environment:
```
conda activate comp3516
```

3. Install required packages:
```
pip install -r requirements
```


## Asking Questions

Should you have any questions, **posting your queries on Moodle** is highly recommended for a couple of reasons. Firstly, articulating your problem in a public forum often helps in organizing your thoughts more clearly, which can be instrumental in finding a solution. Secondly, while lecturers and TAs may not always be available to address your queries immediately, your fellow students who can assist are greatly appreciated.

Empirically, it has been observed that most problems you might encounter have already been resolved online. Therefore, if you face any issue, it's advisable to **first search the web** for solutions. This approach not only saves time but also encourages good practices like consulting manuals/documentation and conducting thorough Google searches for your specific problem.

You are encouraged to share and discuss your thoughts or doubts with your peers. However, it's important to draw a clear line when it comes to sharing answers or code. Any exchange of answers or code is strictly prohibited and, if identified, will be treated as a case of plagiarism. 

## Grading and Submission

In each lab, you will see a tutorial (in `.ipynb`) and several programming tasks (in `*.py`). A clear instruction of the programming tasks is located in a `pdf` file. We recommend you to read the tutorial ahead. You can freely reuse the code in our provided tutorial. Afterward, you will be supposed to implement the programming tasks. In each task, you have to implement several functions in the corresponding file. 

Your grade will depend on the accuracy of your implementation of the programming tasks. For part of the tasks, we will use test cases to grade your code. For the other part of the tasks, we will check the output answer of your code. 

**Please run `python check.py --uid <YOUR_UID>` before submitting.** This script performs automated tests on the examples provided in the docstrings. Failing these tests indicates potential critical issues in your code. Strive to resolve these problems. After that, it will create a zip file named after your `uid`. Make sure you enter the right `uid`. 

Please be aware that successfully passing the checker is not a definitive indicator that you have met all test requirements. Generally, the checker is designed to assess the format of your output, rather than its content. Therefore, it remains your responsibility to thoroughly verify the reliability and accuracy of your code. 

It's important to NOT change the names of any files, including both the zip file and the program files contained within. Altering file names can lead to grading errors. Ensure that all file names remain as they are to facilitate accurate assessment of your work.

Your submission to **Moodle** should consist solely of the **generated `*.zip` file**. It is your responsibility to double check whether your submitted zip file includes your latest work. 

## Office Hour

The office hour of TA is

- Wed 10:30 AM - 11:30 AM
- Fri 10:30 AM - 11:30 AM
  
Please note that these times may be subject to change. Office hours are strictly by appointment. To schedule a meeting, please send an email including your name, a brief description of the topic you wish to discuss, and your preferred time slot. Appointments are crucial; unscheduled visits are considered inappropriate and may not be accommodated. Time slots are allocated on a first-come-first-served (FCFS) basis, and you can expect a reply confirming your appointment within two days.

My office is located in room HW101M, within the HW building, 1st floor. If you have difficulty finding it, especially if it's your first visit, feel free to WhatsApp or email me in advance for assistance.

You can refer to Moodle page for my contact information.

Direct assistance with coding or debugging is NOT provided in office hours.

**Hope you have an enjoyable great journey in this course!**



