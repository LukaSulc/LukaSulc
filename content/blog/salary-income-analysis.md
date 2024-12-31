+++
date = '2024-12-29T18:12:54+01:00'
draft = false
title = 'Your Starting Salary Matters More Than You Think: A Deep Dive into Income Analysis'
+++

## Introduction

When you’re applying for a job one of the most important topics is probably going to be how much you’re going to get paid for your work. An employer offers you a number after which you either accept, reject or, if you’re really dearing, you bargain which may result in you getting higher pay or some additional benefits.

Lately, my friends and I had big disputes over this topic. I was seeking a new job and had rejected multiple employers because of the unacceptably low compensation which doesn’t even cover basic life expenses. The arguments my friends gave me were in the lines of:

> "You’ve got to start from somewhere."

> "The economy is not the best so be happy that you even got the offer."

> "It’s IT, salaries grow fast."

> "Better something than nothing."

To my surprise, many had shared the same thinking even though I didn't have insanely high expectations (like many would expect from an IT person) but rather a slightly above average salary (for our country, that is).

Even though their arguments were somewhat valid, and us talking about it wasn’t going to change anything, I just couldn’t make peace with the whole situation. That’s what motivated me to do a bit of analysis with some highschool maths.

**This analysis is can be applied to any business sector, not just IT.**

## Mathematical Models

Let’s consider a few possible scenarios:

<!-- prettier-ignore-start -->
- Ana (**A**) has a constant salary (\(B_{const}\)) and never gets a raise.
- Bob (**B**) gets a salary percentage increase. Meaning every \(l_{raiseFreq}\) months, the salary from the previous month gets multiplied by a percentage \(p\), with a base/starting salary of \(B_{0}\).
- Chris (**C**) gets a constant salary increment periodically. Meaning every \(l_{raiseFreq}\) months, the salary from the previous month increases by an amount of \(c_{inc}\), with a base/starting salary of \(B_{0}\).

Using these statements let’s create models which will calculate how much income will each of these people acquire after a period of \(x\) months:
\[
\begin{aligned}
A(x) &= B_{const} \cdot x \\
B(x) &= \sum_{n=1}^{x}B_{0}\ \cdot\ p^{\operatorname{floor}\left(\frac{n-1}{l_{raiseFreq}}\right)} \\
C(x) &= \sum_{n=1}^{x}\ \left(B_{0}+\operatorname{floor}\left(\frac{n-1}{l_{raiseFreq}}\right)\cdot c_{inc}\right) \\
\end{aligned}
\]

where \(x\) is a **variable** of time in months and \(B_{const},\ B_{0},\ l_{raiseFreq},\ c_{inc},\ p\) will be fixed **parameters** for each of the graphs.
<!-- prettier-ignore-end -->

These formulas can probably be rewritten to be more concise but I left them in this form because I feel this is how most people would do it on paper.

## “Please skip the formulas”

It may not be clear why I chose these models (A, B, C), but all of them were chosen to reflect real life situations.

#### Linear model (A)

The simplest model is representing a cheap, mean boss that **never gives Ana more** than she already has. While mostly uncommon in real life situations, this will serve as a great "control group".

#### Geometric progression (B)

This is probably the most common form of getting a raise. The employer offers Bob a 12% increase on his current salary, or in other words his new salary will be the **current salary multiplied by 1,12**.

#### Arithmetic progression (C)

The chief gives Chirs a **constant amount increase** every time they have **_the_** meeting. This means that the first raise may be a significant boost to his salary, but after a couple of such raises it will have less of an effect. For example, adding 300 to 1000 is a generous increase of 30%, but adding 300 to 3000 is only 10%!

## Salary analysis

My analysis was done using an online math tool Desmos ([link to my graph](https://www.desmos.com/calculator/bepohmfuus)) so feel free to follow along if the images are not clear. When you get a grasp of what’s going on, you can even change the parameters to do the analysis yourself. For now, it’s important to note that the **x axis** is representing the number of months while the **y axis** is representing the amount of income accumulated over \(x\) months.

The models can be analyzed in two ways:

- Compare each of the models graphically to get a visual picture on how fast they accumulate income compared to each other
- Calculate how much income each of them yields after a period of time

#### Considerations

Comparing the models (with the same base salary), it’s obvious that model A will perform the worst, performance of models B and C will depend on the aforementioned parameters. We could analyse which of the two is better but I think it can portray a wrong picture about the real life situation. Taking into account that our time interval is limited (not planning to work forever), salaries usually hit a ceil at some point (don’t expect to get a raise beyond a certain point) and performance of both models strongly depends on the parameters (Bob having a 10% periodical increase will have a very slow progression compared to Chris getting 300 increase flat).

<!-- prettier-ignore -->
To better portray differences between each of the graphs, some of the **parameters will stay fixed** and x and y coordinates will stay in the **same range**. There’s no point in letting Ana have the same starting salary as Bob and Chris so let’s level the playing field. Ana gets a salary of \(B_{const}=1500\), Bob and Chris start from \(B_{0}=1000\) and they get a raise every \( l_{raiseFreq}=6\) months.

#### Optimistic case (high increase)

<!-- prettier-ignore -->
First, let’s assume Bob and Chris have a great boss. Bob is boosted by 20% (\(p=1.2\)) while Chris gets a bump of \(c_{inc}=300\). Remember, that’s an increase after every six months as stated in the previous paragraph.

{{< figure src="/images/optimistic.png" alt="Graph of models A, B and C with optimistic salary increments" >}}

It's easy to notice that both Bob and Chris surpass Ana as expected, but the interesting part is the amount of time necessary for that to happen. After **25 months**, Bob will have gotten a raise **four** times, ending up with a **salary of 2200**, but still with less money on his account than “poor” Ana. Chris will end up on the top, but only after **4 years** of getting raises.

How much moneyn, you ask? Well let's calculate it:

#### Realistic case (medium increase)

<!-- prettier-ignore -->
In this case Bob and Chris get an increase of (\(p=1.12\)) and \(c_{inc}=200\) respectively. This is a more realistic situation of a good salary increase in the real world. One that many people are usually satisfied with.

{{< figure src="/images/realistic.png" alt="Graph of models A, B and C with realistic salary increments" >}}

Bob will have more money than Ana after **46 months** and Chris will take exactly **3 years**.

#### Usual case (low increase)

<!-- prettier-ignore -->
Lastly, this case portrays what most people have to deal with. An increase of 6% (\(p=1.06\)) or an additional \(c_{inc}=100\) on their salary.

{{< figure src="/images/usual.png" alt="Graph of models A, B and C with usual salary increments" >}}

By the time Bob and Chris catch up to Ana, most people start switching careers. It takes Bob **7 years** to accumulate more than Ana and Chris is going to get there in **5 and a half years** .

#### Comparative analysis

Let’s recap! Ana **didn’t get any salary increase** but spends most of the time with more money then Bob and Chris. This showcases how important it is to negotiate the first salary well, like Ana did, because you will probably end up getting at least some salary increase over the years which extends the intersection of these graphs even more. You might have a bigger salary than your colleagues but **it will take you years to catch up** to the amount of income they accumulated if you started with a significantly lower salary.

<!-- prettier-ignore -->
Another interesting but hidden fact is that comparisons between graphs are preserved regardless of the base salaries, given that the salaries have the same ratio. What I mean by this is that Bob will take the same amount of months to catch up to Ana if the salaries are \(B_{const}=1500, B_0=1000\) or if they are \(B_{const}=2100, B_0=1400\). The ratio in this case is 50% difference (\(B_{const}=1.5 \cdot B_0\)) since [Geometric progression](#geometric-progression-b) increases exponentially. Likewise, Chris will take the same amount of time to catch up to Ana no matter if the salaries are \(B_{const}=1500, B_0=1000\) or if they are \(B_{const}=2100, B_0=1600\). In this case the ratio is the exact amount difference (\(B_{const}=B_0\ +\ 500\)) since [Arithmetic progression](#arithmetic-progression-c) increases linearly.

#### Absolute analysis
