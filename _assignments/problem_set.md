---
type: assignment
date: 2024-03-11
title: 'Problem Set'
pdf: /static_files/problem_set.pdf
# attachment: /static_files/assignments/asg.zip
# solutions: /static_files/assignments/asg_solutions.pdf
due_event: 
    type: due
    date: 2024-04-04T23:59:59
    description: 'Assignment #1 due'
mathjax: true
---
<!-- ## Problem 1: Frequency

**You are required to implement the function in `problem1.py`.**

(1) In Tutorial 1, we showcase that FFT can reveal the frequency of a signal. Please implement function `get_freq_FFT(s_t, f_s)` using FFT algorithm. `s_t` is any time-varient signal, with length `(T*f_s,)`, where `T` is the duration of `s_t`. Please return a numpy array in float with frequencies in ascending order, if there are more than one frequencies. If there are indeed $n$ frequencies, but you can only distinguish some of them, please return `None`. 

(2) In Tutorial 2, we also mention ACF can capture the periodic information of a signal. Please implement `get_freq_ACF(s_t, f_s)` to compute the frequency. Since ACF can only output one frequency, please return the frequency in a numpy array of type float.

(3) For a signal that is the  aggregation of pure tone signals with different frequencies, i.e.
\begin{equation}
    s(t) = \sum_{i=1}^{n} cos(2 \pi \cdot f_i \cdot t),
\end{equation}
where $n$ is the number of frequencies (`n < 1e6`). $f_i$ is the $i$-th frequency. $f_i \neq f_j, \forall i \neq j$. Can you derive an algorithm other than FFT and ACF that extracts the frequency component of $s(t)$? Please implement `get_freq_your_algo(s_t, f_s=16000)`. Note that we assume the frequencies are distinguishable under `f_s` ($f_s \gg 2 \cdot \max(f_i)$). Your goal is to output as many frequency component as possible. Your grade will depend on how many frequencies you can accurately extract. The return value should be stored in a numpy array (float) with ascending order. (You are not allowed to import/use any module for FFT or ACF in (3).)

```
The right answer: [10., 13., 38., 90., 203., 399.]
Your Answer 1: [10.] -> Correct 1, Wrong 0, Miss 5 
Your Answer 2: [10., 90.] -> Correct 2, Wrong 0, Miss 4
Your Answer 3: [10., 12., 13., 15., 30., 200., 399.] -> Correct 3, Wrong 4, Miss 3

```

## Problem 2: Correlation



## Problem 3: Filter
 -->



