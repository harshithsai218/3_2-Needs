# Simpson's Paradox

Simpson's paradox is a statistical phenomenon where the direction of a relationship between variables can change when data is combined or disaggregated. This paradox occurs when groups of data show a certain trend, but when combined, the trend reverses. It is crucial to understand and identify this paradox to correctly interpret data. In simpler terms, it is when the relationship between two variables is not consistent. This paradox is named after Edward Simpson, who first described it in 1951.

## Definition of Simpson's paradox

**Consider n groups of data** such that group $i$ has $A_i$ trials and $0 \leq a_i \leq A_i$ "successes". Similarly, consider an analogous $n$ groups of data such that group $i$ has $B_i$ trials and $0 \leq b_i \leq B_i$ "successes". Then, **Simpson's paradox occurs** if:

$\frac{a_i}{A_i} < \frac{b_i}{B_i} \quad \text{for all } i=1,2,3,\ldots,n$

But, when we aggregate across all groups:

$\frac{\sum_{i=1}^{n} a_i}{\sum_{i=1}^{n} A_i} > \frac{\sum_{i=1}^{n} b_i}{\sum_{i=1}^{n} B_i}$

And **at least one of these inequalities is strict** (meaning that it is not in the equality case). Of course, we could also flip the inequalities and still have the paradox since $A$ and $B$ are chosen arbitrarily. This phenomenon where the relationship between two variables is not consistent is called Simpson's paradox.


## Examples of Simpson's paradox

In the example provided the paradox is demonstrated with a scenario where you and your friend each solve problems on Brilliant. Your friend answers a higher proportion correctly than you on each of two days. However, when the data from both days is combined, you actually solve a higher proportion correctly overall. This showcases how the relationship between individual days and the combined data can differ, leading to Simpson's paradox.

![](img/2024-03-18-22-09-52.png)

Let's revisit the problem accuracy competition example. Over the weekend:

1. **Saturday**:
   - You attempted 8 problems and solved 7 (accuracy: $\frac{7}{8}$).
   - Your friend attempted 2 problems and solved both (accuracy: $\frac{2}{2}$).
   - Your friend had better accuracy.
   
2. **Sunday**:
   - You attempted 2 problems and solved 1 (accuracy: $\frac{1}{2}$).
   - Your friend attempted 8 problems and solved 5 (accuracy: $\frac{5}{8}$).
   - Again, your friend had better accuracy.
   
3. **Overall**:
   - You solved 8 out of 10 problems.
   - Your friend solved 7 out of 10 problems.
   - Despite daily variations, your overall accuracy was higher.

In mathematical terms:
- Your accuracy: $\frac{8}{10}$
- Friend's accuracy: $\frac{7}{10}$

# Correlation and Causation

**Correlation** refers to the existence of a relationship or pattern between the values of two variables. It is often depicted visually through a scatterplot, where data points in the xy-plane can indicate the presence of a correlation. The correlation coefficient ranges from -1 to 1, providing a measure of the strength and direction of the relationship. However, correlation does not imply causation; it simply shows that two variables are related in some way. A correlation can be linear or non-linear, depending on the pattern observed in the scatterplot.

**Causation**, on the other hand, signifies that one event directly influences or causes another event to occur. In a causal relationship, there is an independent variable (the cause) and a dependent variable (the effect). Causation can only be established through appropriately designed experiments that demonstrate a cause-and-effect relationship. It is crucial to differentiate between correlation and causation, as correlation does not imply causation. Understanding the distinction between these concepts is vital in drawing accurate conclusions and making informed decisions based on data analysis.

## Correlation and Causation: A Visual Summary

**Correlation:**
Imagine you have two variables, X and Y, and you're interested in understanding if there's a relationship between them. You can plot them on a graph, with X on the horizontal axis and Y on the vertical axis. Each data point represents a pair of values for X and Y.

Here's an example scatterplot:

```
    Y
    |
    |    ●
    |           ●
    |    ●                ●
    |                 ●
    |          ●
    |                        ●
    |                ●
    |-------------------●-------- X
    |
    |
```

In this scatterplot, you see a general trend where as X increases, Y tends to increase as well. This positive relationship is an example of correlation.

Now, let's consider the correlation coefficient. It quantifies the strength and direction of the relationship between X and Y. If the correlation coefficient is close to 1, it indicates a strong positive correlation. If it's close to -1, it indicates a strong negative correlation. A correlation coefficient close to 0 suggests little to no correlation.

**Causation:**
Causation, on the other hand, implies that changes in one variable directly cause changes in another. It's not enough to observe a relationship; you need to establish a cause-and-effect relationship.

Here's an example:

Let's say you're investigating the relationship between studying hours and exam scores. You might observe a positive correlation – students who study more tend to get higher scores. However, this correlation doesn't necessarily mean that studying more causes higher scores. There could be other factors at play, such as natural aptitude or motivation.

To establish causation, you'd need to conduct experiments. For instance, you could divide students into two groups: one that studies a certain number of hours and another that studies less. Then, you could compare their exam scores to see if the group that studied more indeed achieved higher scores. This experimental design helps establish causation by controlling other variables that could influence the outcome.

**Visual Summary:**

- Correlation: Visualized through scatterplots, indicating the relationship between variables.
- Causation: Established through experiments, demonstrating a cause-and-effect relationship.


# Bayes' Theorem

Baye's theorem states that the probability of an event occurring given that another event has occurred is equal to the product of the probabilities of both events occurring. It is expressed mathematically as:

$P(A | B) = \frac{P(A \cap B)}{P(B)}$

i.e.,

$P(A | B) = \frac{P(A) \cdot P(B | A)}{P(B)}$

- An event $B$ can be explained by a set of exhaustive and mutually exclusive hypotheses $A_1, A_2, \ldots, A_n$.  - Given 'a priori' probabilities $P(A_1), P(A_2), \ldots, P(A_n)$ corresponding to a total absence of knowledge regarding the occurrence of $B$
- And conditional probabilities $P(B \vert A_1), P(B \vert A_2), \ldots, P(B \vert A_n)$, the 'a posteriori' probability $P(A_j \vert B)$ of some event $A_j$ is given by:

$P(A_j \vert B) = \frac{P(A_j) \cdot P(B \vert A_j)}{\sum_{i=1}^{n} P(A_i) \cdot P(B \vert A_i)}$

This formula calculates the probability of event $A_j$ given that event $B$ has occurred, based on the prior probabilities of each hypothesis $A_i$ and their corresponding conditional probabilities of $B$ given $A_i$.

Here's what each component represents:

- $P(A_j | B)$: This is the probability of hypothesis $A_j$ being true given that event $B$ has occurred. It's called the posterior probability.
  
- $P(A_j)$: This is the prior probability of hypothesis $A_j$ being true before observing any evidence.
  
- $P(B | A_j)$: This is the probability of observing event $B$ given that hypothesis $A_j$ is true. It's called the likelihood.
  
- $\sum_{i=1}^{n} P(A_i) \cdot P(B | A_i)$: This term represents the total probability of observing event $B$ over all possible hypotheses $A_1, A_2, \ldots, A_n$. It's calculated by summing the product of the prior probability of each hypothesis and the probability of observing event $B$ given that hypothesis.

**Interpretation:**

Bayes' theorem helps us figure out what's more likely, based on new information. We start with beliefs about different things, and then use the likelihood of new evidence to update them. The result is our new beliefs, which are more likely now.

**Example:**

Let's say we have a medical test for a disease, and we want to know the probability that a patient has the disease given that the test result is positive. Here:
- $A_j$ represents the hypothesis that the patient has the disease.
- $B$ represents the event of getting a positive test result.
- $P(A_j)$ is the prior probability of having the disease.
- $P(B | A_j)$ is the probability of getting a positive test result if the patient has the disease.
- $P(B)$ is the total probability of getting a positive test result.

We can use Bayes' theorem to calculate the posterior probability of having the disease given the positive test result, updating our prior belief based on the test outcome.

Overall, Bayes' theorem is a powerful tool for updating beliefs in the face of uncertainty and is widely used in various fields such as medicine, engineering, and machine learning.


# P-Hacking and Strategies to Avoid It

P-Hacking involves the **misuse of data analysis** techniques to find patterns that appear statistically significant but are not truly meaningful. This practice can lead to false positives and incorrect conclusions in statistical analysis.  

In simpler terms, p-hacking is when someone plays around with data analysis to find results that seem important, even if they're not really meaningful. It's like trying different ways of looking at data until something seems to stand out, even if it's just by chance. This can make it seem like there's a significant finding when there isn't, leading to incorrect conclusions in statistical analysis. So, it's important to be careful and not manipulate data to fit a desired outcome.

- The **p-value**, short for probability value, tells us the likelihood, according to the model in the null hypothesis, of getting a test statistic as extreme as, or even more extreme than, what we observed in the data.

- A small p-value suggests that the tail beyond the observed statistic is small. In other words, the observed statistic is quite different from what the null hypothesis predicts. This indicates that the data provide stronger support for the alternative hypothesis rather than for the null.

- Typically, when the p-value is below 0.05, we consider the result statistically significant. In such cases, we reject the null hypothesis because the data provide strong evidence against it.

## Examples of P-Hacking

Consider we have 5 types of CoronaVirus candidate Vaccines with us for which we need to check which one has actual impact on recovery time of patients. So let’s say we do Hypothesis Tests for all 5 types of vaccines one by one. We set the alpha as 0.05. And hence if P-Value for any vaccine comes less than that, we say we can reject the Null Hypothesis.. Or can we?

![](img/2024-03-18-23-10-10.png)

Say, Vaccine A gives a P-Value of 0.2, Vaccine B gives 0.058, Vaccine C gives 0.4, Vaccine D gives 0.02, Vaccine E gives 0.07.
Now, by above results, a naive way to deduce will be that Vaccine D is the one which significantly reduces recovery time and can be used as the CoronaVirus Vaccine. But can we really say that just yet No. If we do, we might be P-Hacking. As this can be a **false positive**.

One way to avoid P-Hacking is to use **Multiple Hypothesis Testing**. This is when we do multiple Hypothesis Tests and then find the best one. The best one will be the one which has a P-Value less than 0.05.

- One way to tackle this would be to increase the number of tests. So more the tests, more easily you can say that the maximum number of tests are resulting in rejection of Null. 

- But also, more tests will mean that there will be more false positives(5% of total tests in our case). 5 out of 100, 50 out of 1000 or 500 out of 10,000! This is also called the Multiple Testing Problem.

- P-Hacking or Data dredging is a method to misuse the data analysis techniques to find patterns in data that appear significant but are not. This method affects the study negatively as it gives false promises to provide significant data patterns which in turn can lead to a drastic increase in the number of false positives.
