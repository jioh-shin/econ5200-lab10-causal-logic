# Causal Logic and DAGs: Diagnosing Bad Controls

## Objective
I explored how choosing different control variables affects causal estimates and how DAGs can help identify valid controls.

## Methodology
- Ran regressions with different control variables to see how they changed the estimated treatment effect.
- Tested how collider controls and pre-treatment variables can introduce bias.
- Compared total and direct effects by including or excluding a mediator.
- Compared the LaLonde job-training experiment with observational CPS data before and after adjusting for covariates.
- Used `dag_utils.py` to identify valid adjustment sets from a DAG.
- Asked AI to suggest controls for a job-training study, checked its choices against the DAG, and revised my prompt once.

## Key Findings
- Adding a collider control changed the estimate from -0.012 to -0.593 and increased R-squared to 0.585, even though the true effect was zero.
- A pre-treatment control also produced a biased estimate of -0.201 when the true effect was zero.
- The estimated total effect was 3.978, close to the true value of 4.0, while the direct effect was 0.988, close to 1.0.
- The LaLonde experiment had a benchmark effect of $1,794. The observational estimate changed from −$8,498 to $699 after covariate adjustment.
- The AI's first control set gave an estimate of 3.622 compared with the true effect of 4.0. After I revised my prompt, the estimate improved to 4.047.

Overall, I learned that adding more controls does not always improve causal estimates. I also found that checking the causal relationships in a DAG is important, even when the controls are suggested by AI.
