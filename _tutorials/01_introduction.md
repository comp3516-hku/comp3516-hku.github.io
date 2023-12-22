---
type: tutorial
date: 2024-01-26
title: Tutorial 1
# tldr: "Short text to discribe what this lecture is about."
# thumbnail: /static_files/presentations/lec.jpg
attachment: /static_files/tutorials/asg.zip
mathjax: true
---

# Tutorial 1 -- Frequency

In this tutorial, we will guide you through the key components in signal analysis -- frequency. For those who have completed ELEC3241 and ELEC3244, you'll find these concepts familiar and easier to grasp. However, I understand that many of you might be encountering signal processing for the first time in your studies at HKU. Don't worry if that's the case! This lab is designed to be self-contained, ensuring that all students, regardless of their prior exposure to the subject, can follow along comfortably.

## Signal

Let's start by understanding what a signal is. Actually, you are already an expert of signal. Broadly speaking,  a signal encompasses anything that can be perceived, such as images, videos, audio, text, radar, and Wi-Fi signals. The human body itself is an extraordinary signal processing system, continuously adapting to process complex audio and video signals. Mathematically, signal is some function of time that is derived from the physical world, i.e.
\begin{equation}
\mathbf{s} = s(t), \: -\infty < t < \infty.
\end{equation}
Note that the signal is a finite real valued function. These are derived from physical requirement. We use $t$ to denote time. Depending on the nature of $t$, signals can be classified as either analog or digital. An analog signal has a continuous time variable, $s(t)$, while a digital signal features discrete time intervals, represented as $s(n)$, making it suitable for computer processing. The term 'digital' signifies that the continuous time variable $t$ has been quantized into discrete values using specific methods.Normally, we denote $s(t)$ as the signal. Sometimes we refer to $s(n)$ to emphisize the digitality. 

In the realm of signal processing, we view a signal as a function that conveys information about a particular phenomenon. Essentially, any variable quantity that changes over time or space can serve as a signal, facilitating the communication of messages between observers.

**The key question in signal processing is:  how we can model a signal?**. We will illustrate it with a few examples.