# Hypothesis Testing — Is Job Training Worth It?

## Objective
I tested whether a randomized job training program raised participants' earnings, and checked whether the effect was large enough to matter and not only statistically significant.

## Methodology
- Loaded the LaLonde NSW job training experiment, with 445 people: 185 trainees and 260 controls, and used real 1978 earnings as the outcome.
- Plotted the earnings of both groups and compared their means and medians, since earnings are strongly right-skewed.
- Ran a one-sample t-test on the control group's mean earnings against a fixed value.
- Ran a two-sample Welch's t-test comparing trainees and controls, which does not assume the two groups have equal variances.
- Wrote Welch's t-statistic as my own function, welch_t(), and checked it against scipy on the full sample and on five subgroups.
- Computed Cohen's d to measure the size of the effect in standard deviations.
- Ran a power analysis to find the power of this study and the sample size needed to detect an effect of d = 0.3.
- Tested the treatment effect in 5 overlapping demographic subgroups, then applied Bonferroni and Benjamini-Hochberg corrections for multiple comparisons.
- Simulated the distribution of p-values when the null hypothesis is true and when it is false.

## Key Findings
- **Earnings effect:** Trainees earned $1,794.34 more in 1978 than the control group (Welch's t = 2.6741, p = 0.0079), so the difference is very unlikely to be due to chance alone.
- **Effect size:** The Cohen's d was 0.2727, a small effect. A significant p-value says the effect is real, but not whether it is large enough to justify the program's cost.
- **Multiple comparisons:** 2 of the 5 subgroup effects were significant before correction, but only 1 remained significant after the Bonferroni correction. Testing many subgroups makes it easy to find a result by chance, so the corrected results are the ones I would trust.
- **p-value simulation:** When the null was true, the p-values were spread evenly from 0 to 1, so a result below 0.05 still happens by chance. When the null was false, they piled up near 0, and how often they did depended on the study's power.
