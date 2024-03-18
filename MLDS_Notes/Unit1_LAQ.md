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
