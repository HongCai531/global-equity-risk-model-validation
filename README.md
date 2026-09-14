# Global Equity Risk Model Validation

A Python research project evaluating whether more complex correlation models improve global equity risk forecasts.

The study compares CCC-GARCH, DCC-GARCH, diagonal GARCH and EWMA across eight equity markets using rolling weekly forecasts.

## Research question

Does modelling time-varying correlations improve covariance forecasts and portfolio risk estimates relative to simpler alternatives?

## Data and methodology

- Eight markets: US, UK, Germany, France, Hong Kong, India, Brazil and South Africa.
- Weekly observations from 2005–2025.
- Rolling estimation window: 260 weeks.
- Development evaluation: 2015–2019, covering 261 forecast weeks.
- Later historical evaluation: 2020–2025, covering 313 forecast weeks.
- Equal-weight research composite constructed from market log returns.

Each forecast uses only observations available before its target week.

The analysis includes:

- Calendar alignment and missing-data diagnostics.
- GARCH volatility estimation and multi-start DCC optimisation.
- Portfolio QLIKE, multivariate Gaussian loss and variance MSE.
- HAC confidence intervals for model loss differences.
- Gaussian 95% and 99% VaR backtesting.
- Sensitivity checks for mean specification and mismatched return dates.

## Main findings

- DCC did not show a statistically clear improvement over CCC under the evaluated loss metrics in either evaluation period.
- Ignoring cross-market correlations produced substantially more VaR exceptions for the equal-weight composite.
- CCC achieved lower multivariate Gaussian loss than the specified EWMA benchmark in both periods, although portfolio-level comparisons were less conclusive.
- The five largest absolute-return weeks accounted for approximately 84–88% of later-period variance MSE, illustrating its sensitivity to extreme observations.
- CCC and DCC produced identical VaR exception dates at both confidence levels in the later evaluation period.

These findings highlight the importance of model validation and uncertainty, rather than assuming that additional complexity improves forecasts.

## Notebook

See `Global_Equity_Risk_Model_Validation.ipynb` for the analysis, code, tables and figures.

Saved outputs can be viewed without rerunning the notebook. Re-execution requires the input price dataset and the Python dependencies used in the notebook. The dataset is not included in this repository.

## Limitations

- The market universe was selected retrospectively based on data availability.
- Weekly aggregation reduces, but does not eliminate, differences in market closing dates and times.
- The research composite is not an investable portfolio measured in a common currency.
- Gaussian VaR imposes an additional tail-distribution assumption.
- The limited number of 99% VaR exceptions restricts statistical inference.
- The later period is a historical evaluation, not a previously unseen live test.

## Background

This project extends my MSc research with a focus on reproducible implementation, numerical diagnostics and risk model validation.
