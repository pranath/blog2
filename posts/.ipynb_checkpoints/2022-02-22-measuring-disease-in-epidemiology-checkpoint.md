---
aliases:
- /health/epidemiology/2022/02/22/measuring-disease-in-epidemiology
categories:
- health
- epidemiology
date: '2022-02-22'
description: In this article we look at the fundamental tools of Epidemiology (the
  study of disease) essential to conduct studies such as measures to describe the
  frequency of disease, how to quantify the strength of an association, how to describe
  different strategies for prevention, how to identify strengths and weaknesses of
  diagnostic tests, and when a screening programme may be appropriate.
image: https://github.com/pranath/blog/raw/master/images/epidemiology.jpg
layout: post
title: Measuring Disease in Epidemiology
toc: true

---

## Introduction
Since the Covid pandemic which began in 2019, Epidemiology (the study of disease) has become far more mainstream in public discourse and the media. However, this growing interest also comes from the great advances that have been made in the treatment of disease more generally in recent years. While the consequences of Epidemilogical studies have become more and more apparent to the public at large, an understanding of the basic tools and methodology of this discipline are not well understood by the public. In this article we will look at the basic tools of Epidemiology with respect to measuring disease.

## Measures of disease frequency
One of the main objectives of Epidemiology is to describe the frequency of disease in a population. If the variables of interest are continous such as height, then we can use descriptive statistics to describe these such as mean. median, the five number summary, etc. Often the variables of interest are discrete/categorical, e.g. does someone have a disease or not. In these cases, we need measures that can summarise these categoricals. In this section we look at ways to calculate different measures for these categorical type variables such as the prevalence, odds, cumulative incidence and incidence rate.

The appropriate measure can depend on many things such as the context, and what kind of question we are trying to answer.

### Odds

Odds are the ratio of the probabilty of an event to its compliment.

![](https://github.com/pranath/blog/raw/master/images/odds.jpg)

> So for example if the adult population of a village in Tanzania was 6,000 in January 2013. On 1st January, all inhabitants were screened by an infectious disease research team. 800 of the inhabitants were found to be infected with HIV. On 1st April, an additional 300 people were diagnosed with HIV. What are the odds of being HIV-positive on April 1st? 

To calculate the odds of being HIV positive, you need to divide the total number of HIV positive individuals by the number of undiagnosed non-HIV-positive individuals at the specified point of time. By April 1st, a total of 1,100 individuals have been found to be HIV-positive. The remaining 4,900 are not HIV-positive. Therefore, the odds of being HIV-positive on April 1st is 1,100/4,900=0.22.

However this is not the most widley used measure of disease frequency that is used in practice.

### Prevalence

Prevalence is a proportion of individuals in a population who have the disease or attribute of interest at a specific time point. We can think of this measure as a snapshot of the current situation. To calculate prevalence, we divide the number of people with the disease by the total number of individuals in the population.

![](https://github.com/pranath/blog/raw/master/images/prevalence.jpg)

Like Odds, the prevalence is a ratio so can be expressed as a proportion or percentage. However prevalence also requires a specific time point. Because of this, prevalence expresses both the occurence and duration of a disease.

> So for example, say a study on diabetes begins with one thousand 40 to 45-year-old men of which 60 are already diabetic. The remaining 940 men are followed for 5 years during which time 75 men develop diabetes. What is the prevalence of diabetes at the start of the study?

To calculate the prevalence we note there were 60 cases of diabetes at the start of the study and the total population was 1,000. Therefore the prevalence is 60/1,000 which is 6%.

Prevalence and odds can be used to assess the health of a population to plan health services and allocate healthcare resources but also to monitor trends of diseases over time. So, especially prevalence is very useful in epidemiology. However this is not such a helpful to measure diseases of short duration and does'nt help us understand the potential causes of a disease.

### Cumulative Incidence

Sometimes we are not so interested in how many people have a disease at a specific time, but rather how many new cases of a disease we have during a specific time period. Cumulative incidence is a good measure of this, which is the proportion of the population with a new event during a given time period.

![](https://github.com/pranath/blog/raw/master/images/cumulative_incidence.jpg)

This measure refers to new cases, which means that individuals that already have the disease are not included in the numerator (number on top of the calculation).

Cumulative incidence, similar to prevalence, has no units and can take values from 0 to 1, or 0 to 100%, if expressed as a percentage. A cumulative incidence value of 0 means that there were no new cases of the disease during the study period. Whereas, a cumulative incidence value of 1 means that every single individual of the study population developed the disease during the time period of interest.

Cumulative incidence is widely used in epidemiology. It also comes with many names, such as incidence proportion and risk. 

> For example, say a study on diabetes begins with 1000, 40 to 45-year-old men of which 60 are already diabetic. The remaining 940 men are followed for 5 years during which time 75 men develop diabetes. What is the 5-year risk of having diabetes?

The 5-year risk (or cumulative incidence) of having diabetes we can calculate based on there were 75 new cases among 940 men who didn't have the disease when the study started, therefore the risk is 75/940=7.98% over 5 years of follow-up.

We can only calculate cumulative incidence, if there is follow-up of the participants in our study. It is not possible to do so from a survey, which has no follow-up period. Importantly, this follow-up period must be the same for all participants, and no new participants can enter the group during the follow-up.

This is not always possible. There may be loss to follow-up for some subjects or new subjects entering or leaving the study population. There might also be competing risks. For example, in a study where the outcome is cancer diagnosis, someone could get killed in an accident before the end of the follow-up period. This individual would obviously no longer be at risk of cancer. But we don't really know if they would have developed cancer had they not been killed in the accident.

In such cases, cumulative incidence is not well defined. These limitations are important and should be considered when trying to calculate cumulative incidence.

### Incidence rate

Sometimes in real life studies, subjects are lost to follow up or new participants enter or leave the study population at any time, in which cases we cannot use cumulative incidence, however we can use a different measure in these cases called incidence rate.

Incidence rate uses a concept called **person time** which is a measure of the time spent in a study by participants. Each individual contributes person-time to the study during the time they could have developed an event that would have been counted as a case. This means that they contribute person-time from the moment they enter the study until they are diagnosed with the disease of interest, die or are lost to follow-up. Person-time can be expressed in different units. Person-years, person-days, person-hours, etc.

Incidence rate can take values from zero to infinity and it is always expressed per unit of person-time.

![](https://github.com/pranath/blog/raw/master/images/incidence_rate.jpg)

> For example, say a population of 100 healthy women was followed up for the development of breast cancer. 20 women were followed‐up for 1 year and were then lost to follow‐up. After being followed-up for 5 years, 10 women developed breast cancer. The remaining women who never developed breast cancer were followed for 10 years. What is the incidence rate of breast cancer in this population? 

First, you need to calculate the total number of person-years, which equals to 20x1 for the women followed up for 1 year and then lost to follow-up, plus 10x5 for the 10 women who developed breast cancer after being followed for 5 years, and finally plus 70x10 for the remaining who were followed for 10 years. This results in 20 + 50 + 700= 770 person-years. The number of cases over the follow-up period was 10. Therefore, 10/770=0.013 = 13 cases of breast cancer per 1,000 person years during the follow-up period.

The word *rate* is surprisingly often used inappropriately to describe measures that are clearly risks i.e. ratios. So, be aware when you come across this term. Incidence rate is extremely useful. It accounts for the time of follow-up and for the time when the new event occurred. It is also suitable for studies where participants enter or leave the study at different times and it can deal with loss to follow-up and competing risks. Therefore, it can be used even when cumulative incidence is problematic or cannot be properly defined and is a powerful tool to describe the occurrence of a disease in the population.

## Measures of association

While measuring the occurance of disease in a population is valuable, some of the greatest contributions Epidemiology has made is to understanding the causes of disease. In epidemiological research, we typically compare two populations with each other, with regard to exposure and outcome. We call exposure, any potential causal characteristic such as behaviors, environmental factors, treatments, occupation, genetic factors, and so on. The outcome is most often a disease.

The only way to be certain of a causal relationship is to use exactly the same population to both expose a patricular factor that might cause a disease and also not expose them to this factor, yet this is difficult to do in practice. So we have to compare different populations that are exposed and not exposed to a factor, but this means we need to be cautious about what conclusions we can draw. If the two populations are very similar, then we can have more confidence in attributing causality to a particular factor.

The statistical analysis of data generated by epidemiological studies can only provide you with evidence that, an association between the exposure and the outcome exists. It is up to you then, to decide whether it is reasonable to take the extra mental step and declare with little or much confidence that the exposure is what causes the outcome. To sum it up in a sentence, you should always keep in mind that association does not necessarily imply causation. Epidemiological knowledge is essential to decide when association implies causation.

We use measures of assocation for causal inferences and assocations between variables. They can be divided in two broad categories, relative and absolute measures. 

### The 2x2 Table

Epidemiological studies typically examine the association between an **exposure** and an **outcome**. There are, of course, many variations of this and, depending on the context and the study design, the research question might look completely different.

When you are faced with such a study, you can split the participants in the study into two groups, based on the exposure. Some of them are or have been exposed to the exposure of interest ('exposed' group), while the rest are not or have never been exposed to it ('unexposed' or 'non-exposed' group).

Similarly, the same participants can be split into two groups using the outcome, which is frequently a disease, as a criterion. Some of them have the disease, while the rest do not have the disease.

An easy way to represent these groups is using a 2x2 (two-by-two) table, which you will come across very often in Epidemiological studies. A 2x2 table provides a clear format to present the data and makes calculation of measures of frequency and association much simpler. In general, a 2x2 table would look like this:

![](https://github.com/pranath/blog/raw/master/images/2x2table.jpg)

> For example, consider a study where 500 people, 200 smokers and 300 non-smokers, were followed up for 10 years. The primary outcome of the study is chronic lung disease. Among smokers, 50 developed chronic lung disease. Among non-smokers, 60 developed chronic lung disease. How would you present your data in a 2x2 table? 

Using the templates above, you can populate the cells like this:

![](https://github.com/pranath/blog/raw/master/images/2x2table-complete.jpg)

### Relative measures of assocation

Relative measures of assocation are basically all ratios, Relative measures include the risk ratio, the incidence rate ratio, and the odds ratio.

### Risk ratio

The risk ratio is a relative measure of assocation. For the risk ratio or cumulative incidence ratio, the numerator is the risk in the exposed group, and the denominator is the risk in the unexposed group, and you divide one by the other. You always need to mention the time period you are referring to when quoting a risk ratio.

![](https://github.com/pranath/blog/raw/master/images/risk_ratio.jpg)

The question is, how do you interpret the risk ratio? The key value of a risk ratio, of any ratio really, is one. A risk ratio of one means that the risk of disease among the exposed is equal to the risk among the unexposed. Which makes perfect sense, we get a value of one when the numerator and the denominator are equal. If the risk ratio is higher than one, it means that the risk of disease among the exposed is greater than the risk among the unexposed. Finally, a risk ratio lower than one means that the risk of disease among the exposed is smaller than the risk among the unexposed.

> For example. say of  600 people aged >50 years who had high blood pressure, 35 experienced a stroke within 10 years of follow-up. Among 3,250 people who had low blood pressure, 40 experienced a stroke within the same follow-up period. What is the risk ratio of having a stroke among people with high blood pressure compared to those with low blood pressure?

Risk ratio is calculated by dividing the risk of an event in the exposed group by the risk of an event in the unexposed group. RR = (35/600) / (40/3250) = 4.74   

If we wish to express this in terms of association, a risk ratio of one means that the exposure is not associated with a disease. A risk ratio higher than one means that the exposure is associated with an increased risk of the disease. And a risk ratio lower than one means that the exposure is associated with a decreased risk of the disease. 

### Incidence rate ratio

The Incidence rate ratio is a relative measure of assocation. The incidence rate ratio is calculated by dividing the incidence rate among the exposed by the incidence rate among the unexposed. 

![](https://github.com/pranath/blog/raw/master/images/irr_ratio.jpg)

The interpretation is similar to the risk ratio e.g. an Incidence rate ratio of 1 indicates no assocation.

> For example, A cohort study is conducted to determine whether hormone replacement therapy is associated with an increased risk of coronary artery disease in adults over the age of 40. The study found that the frequency of coronary artery disease amongst those using hormone replacement therapy was 27 per 1,000 person-years. The study also found that the frequency of coronary artery disease amongst those not using hormone replacement therapy was 3 per 1,000 person-years. What is the incidence rate ratio?

The incidence rate ratio is calculated by dividing the incidence rate among the exposed by the incidence rate among the unexposed so 27/1000 divided by 3/1000, so 0.027 / 0.003 = 9. 

### Odds ratio

The Odds ratio is a relative measure of assocation. To get the odds ratio you need to divide the odds of having the disease among the exposed by the odds of having the disease among the unexposed.

![](https://github.com/pranath/blog/raw/master/images/odds_ratio.jpg)

The interpretation is similar to the risk ratio e.g. an Odds ratio of 1 indicates no assocation.

### Absolute measures of assocation

Absolute measures of association quantify the actual absolute differences between the groups. This can be very informative when considering the impact of a factor at the population level. These measures include risk difference and the incidence rate difference.

### Risk difference

The risk difference is simply the numerical difference of the risks in the two groups. In other words, the risk among the exposed minus the risk among the unexposed. 

![](https://github.com/pranath/blog/raw/master/images/risk_difference.jpg)

The key value of the risk difference and of the incidence rate difference is zero. When the risk of the disease among the exposed is equal to the risk among the unexposed, the risk difference is zero. Compare these with the ratios where the value indicating no difference between the two groups is one. If the risk difference is higher than zero, it means that the risk of disease among the exposed is greater than the risk among the unexposed. In contrast, when the risk of disease among the exposed is smaller than the risk among the unexposed, the risk difference is a negative number. 

Focusing on the concept of association, we would say that the risk difference of zero means that the exposure is not associated with disease. A positive risk difference means that the exposure is associated with an increased risk of the disease, and the negative risk difference that the exposure is associated with a decreased risk of the disease. 

> For example, In a cohort study, of 1,000 women who took oral contraceptives as a method of birth control, 50 developed ovarian cancer. A comparison group consisted of 1,700 women who did not take oral contraceptives. During the follow-up period, 25 women developed ovarian cancer in the comparison group. What is the Risk Difference for ovarian cancer among women who took oral contraceptives compared to women who did not?

Risk difference is the risk among the exposed minus the risk among the unexposed. RD = (50/1,000) - (25/1,700) = 0.035 over the study period. 

### Incidence rate difference

The Incidence rate difference is obtained by subtracting the incidence rate among the unexposed from the incidence rate among the exposed over a certain period. 

![](https://github.com/pranath/blog/raw/master/images/ird.jpg)

The interpretation is the same for the risk difference i.e. an Incidence rate difference of zero means the risk of the disease among the exposed is equal to the risk among the unexposed for the given period.

> For example, In a study investigating obesity and myocardial infarction (MI), the following results were obtained. Amongst participants with obesity, a total of 80 MI occurred. Amongst normal weight participants, a total of 40 MI occurred. The group with obesity accumulated 90,000 person-years and the normal weight group 175,000 person-years during the study period. What is the incidence rate difference? (per 100,000 person-years)

To calculate the incidence rate difference, you need to subtract the incidence rate among the unexposed from the incidence rate among the exposed. (80/90,000) - (40/175,000) = 0.00066032 x 100,000 = 66.03 per 100,000 person-years.   

### When to use Relative vs Absolute measures of assocation

#### Risks and Rates

Let's begin by considering the differences between risks and rates. Risk is based on a proportion of persons with disease or outcome of interest, as expressed as a percentage. It is also known as cumulative incidence because it refers to the occurs of disease in a group studied over time. Therefore, it is calculated by taking the total number of new cases and dividing it by the population at risk at the beginning of the observation period.

But there are difficulties to calculate this in practice, as highlighted earlier e.g. we would need to catch everyone in the follow up and often people are lost due to leaving the area, or dying. If someone dies for example, how can we know if they might have got the disease or not if they lived?

Also, many diseases can occur more than once and we have to decide how to handle reocurrences. If you include them, the incidence proportion could exceed one. While if you accept only first diagnosis, you may underestimate the true burden of disease.

An alternative is to express incidents as a rate, which is the number of new cases divided by the total person time at risk for the population. As we have seen, person time is calculated by the sum total of time all individuals remain in the study without developing the outcome of interest.

Like cumulative instance or risk, incidence rates also measure the frequency of new cases of disease in a population. But take into account the sum of the time that each participant remained under observation and at risk of developing the outcome under investigation.

You can only calculate an incidence rate if you have periodic follow-up information on each subject. Including not only if they develop the outcome, but also when they developed it.

Cumulative incidence and incidence rates also differ on the range of values they can take. Risk must be a proportion. Therefore, it must be between 0 and 1 and reported as a percentage. Rates, on the other hand, are not restricted between 0 and 1. **To sum up, cumulative incidence is useful when you want to describe the incidence of disease in a country, but do not have detailed information on each and every member of the population.**

> For example, In a study investigating obesity and myocardial infarction (MI), the following results were obtained. Amongst participants with obesity, a total of 85 MIs occurred in 99,573 person-years. Amongst participants with normal weight, a total of 41 MIs occurred in 177,356 person-years. What is the incidence rate difference per 100,000 person-years?

You can calculate the incidence rate difference by subtracting the incidence rate among the unexposed from the incidence rate among the exposed. Incidence rate difference is: (85/99,573) - (41/177,356) = 0.000622 multiplied by 100,000 = 62.2 per 100,000 person-years.     

#### Ratios and differences

Ratios are also known as relative risk comparisons. Relative risk comparisons and risk differences, essentially provide two different perspectives on the same information. Ratios provide a measure of the strength of the association between a factor, and a disease or outcome. They are calculated by dividing the cumulative incidence, or incidence rate in the exposed group, by the cumulative incidence or incidence rate, in the unexposed group. 

On the other hand, risk or rate differences, provide a measure of the public health impact of the risk factor. and focus on the number of cases that could potentially be prevented, by eliminating the risk factor. 

> For example, If the risk difference in a cohort study on smoking and lung cancer was 70 per 1,000 individuals over a 10-year period, how would you interpret this result?

If smoking is a cause of lung cancer, then smoking caused 70 excess cases of lung cancer in a 10-year period in a population of 1,000 smokers. Risk difference calculates the excess risk of the outcome among the exposed compared to the unexposed.

## Attributable risk

Published studies often report the magnitude of the association they investigate, which is clearly important when trying to identify causal links. Sometimes though, what we are interested in is the impact of a factor or of a disease on the population as a whole. This is when the concepts of attributable risk and of population attributable risk can be very useful. These measures quantify the population impact of a health-related factor and therefore are particularly useful for health policy. 

Attributable risk is a measure of the public health impact of an exposure on the exposed group. In other words, it quantifies the answer to the question, "If we remove the exposure, how much would the disease burden be reduced?" This information will be critical in prioritizing public health interventions.

Attributable risk is essentially the risk or incidence rate difference. When we speak of attributable risk though, instead of risk difference or incidence rate difference, we imply that there is a causal relationship between the exposure and the outcome. We also assume that there are no other sources of bias and the distribution of all other known and unknown factors that influence risk is the same in the exposed and the unexposed. 

![](https://github.com/pranath/blog/raw/master/images/attributable_risk.jpg)

![](https://github.com/pranath/blog/raw/master/images/attributable_risk_percent.jpg)

Another concept linked to the attributable risk is the number needed to treat, which is the inverse of the attributable risk. The number needed to treat is very relevant when testing the effectiveness of health interventions and treatments.

Attributable risk and attributable risk percent are quite easy to calculate. They can be really helpful when you need to consider the effect of an exposure among the exposed group, which is something that happens all the time in public health.

> For example, A prospective cohort study of smoking during pregnancy and low birth weight of new-born infants showed an attributable risk of 42%; mothers who did not smoke during pregnancy were used as the reference category. Assuming the relationship between smoking during pregnancy and low birth weight is causal this suggests that?

This suggests that 42% of low birth weight babies from mothers who smoked during pregnancy could have been avoided if they had not smoked during pregnancy. Attributable risk assesses how much the burden of disease can be avoided if the exposure was removed.

### Population attributable risk

Attributable risk is a great tool for public health. But as we know, it exclusively refers to the exposed group of people. Sometimes we're interested in quantifying the effect of an exposure on the entire population, and not only on those exposed to it. This is when population attributable risk can be useful.

Population attributable risk is the excess risk of disease in the total study population that is attributable to the exposure. The total study population includes both exposed and unexposed individuals. Once you know the numerical value of the attributable risk, you only need to multiply it by the prevalence of the exposure in the population, and you can easily calculate the population attributable risk. 

![](https://github.com/pranath/blog/raw/master/images/par.jpg)

![](https://github.com/pranath/blog/raw/master/images/par2.jpg)

![](https://github.com/pranath/blog/raw/master/images/par3.jpg)

In contrast to the attributable risk which focuses on the exposed group, this provides an insight into the entire population which is frequently what we're interested in. The population attributable risk percent depends on both the prevalence of the exposure and the strength of the association. 

Attributable risk and population attributable risk provide valuable information about the magnitude of the impact of an exposure which cannot be captured by relative measures of association. This is the kind of information you would need if you wanted to prioritize public health interventions and maximize the benefit for the population.

> For example, Which measure would be the most appropriate to provide insight on the impact of an exposure on a population?

Population Attributable Risk is an expression of the impact of the exposure in the entire population.

## Summary of Measures in Epidemiology

We can divide measures in Epidemiology in three broad categories: measures of frequency; measures of association; and measures of impact. There is some overlap between measures of association and measures of impact, as attributable risk is essentially the risk (or incidence rate) difference.

![](https://github.com/pranath/blog/raw/master/images/epidemiology_measures_overview.jpg)

## Strategies for prevention

The classic article in epidemiology ['Sick individuals and sick populations' by Geoffrey Rose](https://academic.oup.com/ije/article/30/3/427/736897) highlights important considerations between different approaches for prevention.

High-risk strategies target individuals or groups that have been identified as having the highest risk of disease and would benefit the most from prevention. On the other hand, population strategies target the entire population, regardless of whether individuals are exposed to risk factors or are “at-risk”. 

In Rose's paper he highlights the **prevention paradox** which is, a large number of people exposed to low risk generate more cases than a small number of people exposed to high risk, which is counter-intuitive. This observation has substantial implications for policy, because a measure that brings large benefits to the community offers little to each participating individual, which is one of the main reasons why public health is such a complex endeavor. 

## Disease detection

The measures of frequency and association that we have seen so far are typically calculated under the assumption that we accurately measure the exposure and the outcome. This is not always true. 

The measurement tools and diagnostic methods we have at our disposal may lead to erroneous judgments regarding the status of individuals; for example, whether they are sick or healthy. Here we will consider methods available to quantify the inaccuracy of the diagnostic tests and how these can inform clinical and policy decisions, including considerations about screening programs. 

### Sensitivity and Specificity

Given tests are imperfect, we can quantify the degree of error of a test using these 2 measures.

Consider the confusion matrix for a test, which describes all the possible outcomes of a test.
The test results in either a positive or negative indication for a disease, and that test result is either accurate or true or not accurate and false. This leads to 4 possible outcomes of a test which is our confusion matrix.

- True Positives (TP) Correctly diagnosed by the test as having the disease
- True Negatives (TN) Correctly diagnosed by the test as not having the disease
- False Positives (FP) Incorrectly diagnosed by the test as having the disease
- False Negatives (FN) Incorrectly diagnosed by the test as not having the disease

![](https://github.com/pranath/blog/raw/master/images/confusion_matrix_disease.jpg)

The sensitivity or true positive rate is calculated by TP/(TP+FN)
This could be seen as a measure of 'How much confidence can we have when your test says you have a disease that you really have it'.

The specificity or true negative rate is calculated by TN/(TN+FP)
This could be seen as a measure of 'How much confidence can we have when your test says you don't have a disease that you really don't have it'.

> For example, A biomarker is used to detect subclinical cases of prostate cancer. Which metrics are NOT influenced by the prevalence of the disease in the population that is being tested? 

This would include Sensitivity and Specificity because there are about the accuaracy of the test itself.

These measures can be very useful for evaluating a diagnostic test. These two measures describe characteristics of the test itself.

These are the same concepts we would use in Data Science and machine learning, with a classification model for example.

### Predictive Values

Another pair of metrics valuable in evaluating the performance of diagnostic tests, consists of the positive predictive value and the negative predictive value.

When comparing the true disease status with the result of the diagnostic test, we can have four possible combinations. True Positive, False Positive, False Negative and True Negative. We have already seen how to calculate sensitivity and specificity using the true disease status as the denominator. What if we use the test results as a denominator? The proportion of positive tests that correctly identified diseased individuals, is called Positive Predictive Value. In other words, positive predictive value is the proportion of True Positives among all positive results. The proportion of negative results that correctly identify non-diseased individuals is called Negative Predictive Value. 

![](https://github.com/pranath/blog/raw/master/images/predictive_values.jpg)

Positive Predictive Value (PPV) is calculated by TP/TP+FP

> For example, A new blood test is proposed for early diagnosis of prostate cancer. Results of the new test are compared with the method that is considered the gold standard to diagnose this type of cancer. 1,000 men were tested with both methods. Among those who had prostate cancer (according to the gold standard method), 200 tested positive in the new test and 180 tested negative. Among men who did not have prostate cancer (according to the gold standard method), 570 tested negative and 50 tested positive. What is the positive predictive value of the new test?

Positive predictive value is the proportion of true positives among all positive results. PPV=TP/(TP+FP) where TP is true positives and FP is false positives. Therefore, PPV= 200/(200+50)=0.80=80%.

Negative Predictive Value (NPV) is calculated by TN/TN+FN

These definitions reflect a population-based view of the diagnostic test results.

We can also consider it from the perspective of someone who takes the test: if the test result is positive then the PPV is the probability that they has the disease if the test result is positive. If the test result is negative, then the NPV is the probability that they do not have the disease.

> For example, Your aunt is 50 years old and, following her physician's advice, she had a mammography screening done, which was negative. The physician told your aunt that this test is used for early detection of breast cancer and since the test was negative, she shouldn't worry about breast cancer at the moment. Your aunt knows you have studied epidemiology and she asks you how likely it is that she does not have breast cancer. Searching the literature, you find that mammographies have a sensitivity of 70% and specificity 80%, and 3 in 10 women aged 50 years old have breast cancer. What's your answer to your aunt?

To give an individual answer for your aunt about her negative result we can use the Negative Predictive Value (NPV) of the test in this population, as well as a confusion matrix to establish the figures we need. If we say 1,000 50-year old women had mammography screening, we can then calculate figures for each of the 4 possibilities of the test (TP, FP, TN, FN) using the fact we know 3/10 women have cancer, and 7/10 don't have cancer, and complete the confusion matrix that would lead to the values of sensitivity and specificity we have been given. We can then use these derived confusion matrix values to calculate the NPV. 

Our assumed population is 1,000, and 3/10 women have cancer so we have 300 with cancer in total and 700 without cancer in total. 

We know our test sensitivity (our true positive rate of our test) is 70% so when our test is applied to those 300 with cancer we will get the following:

TP = 300 x 0.7 = 210
FN = 300 - TP = 90

We know our test specificity (our true negative rate of our test) is 80% so when our test is applied to those 700 without cancer we will get the following:

TN = 700 x 0.8 = 560
FP = 700 - TN = 140

We now have all 4 values of the confusion matrix.

Thus, NPV = TN/(TN+FN) = 560/(560+90) = 0.86 i.e. the probability that your aunt does not have cancer is 86%.

**Sensitivity and Specificity describe characteristics of the test itself and do not vary with the prevelence of the disease in the population, wheras PPV and NPV heavily depend on the prevelance of the disease in the population.**

This means there can be big differences between the accuracy of the test itself, and the outcome of the test for an individual taking the test. Consider the following:

![](https://github.com/pranath/blog/raw/master/images/sens_v_pred.png)

So even an excellent diagnostic test, with 100 percent sensitivity, and 99.9 percent specificity, can yield a positive predictive value as low as 50 percent, when the disease is very rare with a prevalence of 0.1 percent. A positive predictive value of 50 percent means that half of the positive tests are wrong, which is a pretty terrible outcome. The same test when applied to a population where the disease prevalence is 10 percent, yields a positive predictive value of 99 percent. 

PPV and NPV give information about the effectiveness of a test **within a specific context**. They also help you interpret the result from the perspective of the individual who took the test, which is critical for clinical work as well as for policy decisions.

### Receiver Operative Characteristic (ROC) Curve

Many biological variables, such as cholesterol or blood pressure are measured in a continuum, and there is no clear threshold below or above which someone should be definitely considered healthy or sick. However, we tend to set such thresholds for practical reasons, especially in clinical practice. Similarly, many diagnostic tests provide measurements the numerical values of which cannot clearly distinguish between healthy and sick individuals.

The Receiver Operative Characteristic (ROC) curve is a tool which helps determine how well a diagnostic test is able to discriminate sick from healthy individuals. ROC curves are also used to decide on the optimal threshold for diagnosis. 

To do this, we must plot the sensitivity against the false positive rate (i.e. 1 minus the specificity) for every possible threshold for a test or a combination of tests. This curve allows us to understand the trade-off between sensitivity and specificity depending on the threshold for diagnosis. Ideally, you want to pick a threshold which has the optimal combination of high sensitivity and low false positive rate.  

In most circumstances, the closer the ROC to the top-left hand corner of your graph, the more accurate the test is overall. The area under the curve can also be used to calculate the accuracy and usefulness of a test. In other words, the larger the area under the curve, the better the test. The ROC curve is a helpful tool used to evaluate diagnostic tests, although, as you already know non-statistical considerations should also be taken into account.

![](https://github.com/pranath/blog/raw/master/images/roc.png)

## Screening

According to the World Health Organization:

> Screening is the presumptive identification of unrecognized disease in an apparently healthy, asymptomatic population by means of tests, examinations, or other procedures that can be applied rapidly and easily to the target population.

Firstly, people who participate in screening are classified as either unlikely, or possibly having the disease of interest. This is something that most participants in screening programs do not realize. The definition also refers to unrecognized disease and apparently healthy asymptomatic people. This is very important to understand. We speak of screening only when people without symptoms are targeted. This is a very reasonable conduct screening to detect disease that has not yet shown any symptoms.

Screening is applied to populations in the sense that it targets entire subgroups of the population, and not a small number of individuals that may visit the doctor for some reason. The final part of the World Health Organization's definition refers to tests or examinations that can be applied rapidly and easily. This is a key element of any screening program. Exactly because it targets many and mostly healthy individuals, the diagnostic test must be easy, quick, and not really costly. Screening has a huge potential to save lives and technological advances have made it a feasible option for an increasing number of diseases.

Screening seems to be a great idea. The objective is to reduce mortality and morbidity by early detection and treatment of a disease. However, even when the outcome of interest is as straightforward as mortality, evaluating a screening program can prove really difficult.

These challenges, methodological, financial, practical, and ethical, is why there is so much debate even around screening for breast and prostate cancer, which have been running for decades in many countries.

## Conclusion

In this article we have looked at measuring disease frequency and association and on using these measures to inform decisions about screening and prevention. We have learned that there are different measures of disease frequency and association. 

A rate provides more information than a risk, but requires more detailed follow-up.

A relative measure of association is great when exploring causality. But an absolute measure can better describe the impact on the population.

The correct interpretation of such measures is key to understanding research and potential implications for public health, for example when we looked at the high risk and population approaches to prevention. We have also learned about inaccuracies in disease detection, and how to quantify misclassification and how it can affect individual diagnosis and screening programs.

We also made the distinction between association and causation, and this helps us engage critically with the literature and consider the strengths and limitations of research studies.
 
For further reading on Epidemiology you can refer to the free online book ['Basic Epidemiology 2nd edition' by the World Health Organisation](http://apps.who.int/iris/bitstream/handle/10665/43541/9241547073_eng.pdf;jsessionid=E61B0E8F8FFE6A6752B35CC04E7F8493?sequence=1).