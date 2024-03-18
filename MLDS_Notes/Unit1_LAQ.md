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