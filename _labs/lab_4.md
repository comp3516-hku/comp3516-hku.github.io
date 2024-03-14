---
layout: lab
type: lab
date: 2024-02-21
title: 'Lab #4 Filtering'
# pdf: /static_files/assignments/asg.pdf
attachment: /static_files/lab_4_release.zip
# solutions: /static_files/assignments/asg_solutions.pdf
due_event: 
    type: due
    date: 2024-03-02T23:59:59
    description: 'Lab #4 due'
mathjax: true
---
## Task 4-1: Frequency Filter(30 points)

**You are required to implement the functions in `task_4_1.py`**.

Given a noisy signal, you are supposed to apply different filters accordingly. You are asked to use 5-order Butterworth filter. You are **NOT** allowed to directly use either band-pass filter or band-stop filter.

1. Apply a high-pass filter with cutoff frequency 20Hz.
2. Apply a low-pass filter with cutoff frequency 10Hz.
3. Apply a band-pass filter with cutoff frequency [10, 20]Hz. You should use low-pass and high-pass filter to implement this band-pass filter. 

The sampling rate `self.fs` is 500 Hz. You should return the filtered signals.




## Task 4-2: Apply Filters I (30 points)

**You are required to implement the functions in `task_4_2.py`**.

In this task, you are now given multiple noisy signals. Please use the filters that have been included in our tutorials to smooth these noisy data.

1. `task_4_2_1.pickle`: You are supposed to filter it in `apply_filter_1()`. The sampling rate is 10Hz.
2. `task_4_2_2.pickle`: You are supposed to filter it in `apply_filter_2()`. The sampling rate is 20Hz.


**Note**: You can pick the filters according to the shape of the signals. Smoothing is a quite subjective task, but  as a programming task, we have some quantitative metrics.  The data for Task 4-2 are synthetic, meaning we possess the original datasets without any added noise. This allows for a direct comparison between the filtered output and the true, noise-free signal to objectively evaluate the effectiveness of the filtering process. Therefore, we can evaluate your results using the following metrics:

- SNR (Signal-to-Noise Ratio): This measures the level of the desired signal relative to the background noise. A higher SNR means the signal is clearer compared to the noise.
- RMSE (Root Mean Square Error): RMSE quantifies the difference between values predicted by a model or filter and the values actually observed from the environment that is being modeled or about which predictions are being made. Lower RMSE values indicate a closer fit to the original data.
- Variations of the first derivative:  This metric assesses the smoothness of a signal by measuring the changes in its rate of change. Smoother signals have less variation in their first derivative.
  
**Implementation of these metrics is not required.**

## Task 4-3: Apply Filters II (40 points)

**You are required to implement the functions in `task_4_3.py`**.

In this task, you will work with several ECG clips. An ECG period can typically be divided into several key sections: the P-wave, the QRS-complex, and the T-wave. The QRS complex, in particular, signifies the electrical activation leading to the contraction and expulsion of blood from the ventricles of the heart. Numerous methods have been developed to extract these components, but our focus will be on isolating the R-peaks. A simple ECG illustration is provided below for reference.
![Alt text](data/ecg_illu.png)

In this task, you are required to write a function `ecg_analysis()` for analyzing ECG signals. This function should compute:

- Heart Rate (HR): Compute and return the heart rate in beats per minute (BPM). You have the option to segment the data with a window and calculate the average or to derive the heart rate across the entire dataset.
- RR-intervals: You should identify all R peaks in the ECG signal. Once R peaks are identified, calculate the time difference between each consecutive pair of R peaks.
- Heart Rate Variations (HRV): It is a measurement of RR-intervals. Here you are asked to calculate RMSSD (root mean square of successive differences). Given several R-peaks $[R_1, R_2, \cdots, R_n]$, we can get RR-intervals $[RR_1, RR_2, \cdots, RR_{n-1}]$ by calculating $R_{i+1} - R_{i}, 1 \le i \le n-1$. Then RMSSD is calculated as 
$$
\operatorname{RMSSD} = \sqrt{\frac{1}{n-2} \sum_{i=1}^{n-2}(RR_{i+1}-RR_{i})^2}
$$
where $n$ is the number of R-peaks. In this task, we use all the R-peaks in the data clip without adding sliding windows.

You should preprocess your ECG data by removing unexpected noise. Previous analysis skills (such as FFT and ACF) might be useful for you as well. After you get the R-peaks, it would be beneficial to check (and possibly remove) the outliers.

Your `ecg_analysis()` function must be generalizable, meaning it should be capable of analyzing any given ECG clip rather than being tailored to specific datasets. We will test your result not only on provided dataset but also on some unforeseen data.

You are allowed to use ONLY the functions that we include in the tutorials (i.e. `numpy`, `scipy`, `hampel`, `matplotlib`). Other modules are strictly forbidden.

## How to submit

**Please run `python check.py --uid <YOUR_UID>` before submitting.** This script performs automated tests on the examples provided in the docstrings. Failing these tests indicates potential critical issues in your code. Strive to resolve these problems. After that, it will create a zip file named after your `uid`. Make sure you enter the right `uid`. 

It's important to avoid changing the names of any files, including both the zip file and the program files contained within. Altering file names can lead to grading errors. Ensure that all file names remain as they are to facilitate accurate assessment of your work.

Your submission to **Moodle** should consist solely of the **generated `*.zip` file**. It is your responsibility to double check whether your submitted zip file includes your latest work. 