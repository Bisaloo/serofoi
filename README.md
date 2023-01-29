
## *serofoi* <img src="man/figures/serofoi-logo.png" align="right" width="120" />

An R package to estimates the *Force-of-Infection* of a given pathogen
from population based sero-prevalence studies on a Bayesian framework.

<!-- badges: start -->

[![License:
MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![R-CMD-check](https://github.com/epiverse-trace/readepi/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/epiverse-trace/readepi/actions/workflows/R-CMD-check.yaml)
[![Codecov test
coverage](https://codecov.io/gh/epiverse-trace/readepi/branch/main/graph/badge.svg)](https://app.codecov.io/gh/epiverse-trace/readepi?branch=main)
[![lifecycle-concept](https://raw.githubusercontent.com/reconverse/reconverse.github.io/master/images/badge-concept.svg)](https://www.reconverse.org/lifecycle.html#concept)
<!-- badges: end -->

## Installation

You can install the **development version** of `serofoi` from
[GitHub](https://github.com/) with:

``` r
# install.packages("remotes")
remotes::install_github("TRACE-LAC/serofoi")
```

## Quick start

These examples illustrate some of the current functionalities:

```{r example}

##library(serofoi)

remotes::install_github("TRACE-LAC/serofoi", ref = "dev-zulma", force = TRUE)

library(serofoi)

# Prepare the data for using serofoi

data_test <- prepare_data(mydata)


# Current version of the package runs three different models of the FoI

# Constant Force-of-Infection with a binomial distribution
model_0 <- run_model(model_data = data_test,
                     model_name = "constant_foi_bi")

# Time-varying Force-of-Infection with a prior normal-binomial distribution
model_1 <- run_model(model_data = data_test,
                     model_name = "continuous_foi_normal_bi")

# Time-varying Force-of-Infection with a prior normal-log distribution
model_2 <- run_model(model_data = data_test,
                     model_name = "continuous_foi_normal_log")


# For each model, you can use ploting functions such as
plot_model(model_0, size_text = 6)
plot_seroprev(model_0, size_text = 6)
plot_foi(model_0, size_text = 6)
plot_rhats(model_0, size_text = 6)
extract_summary_model(model_0)

# You can compare these three models based on convergence, elpd and p-values
comp_table <- get_comparison_table(
  model_objects_list = c(m0 = model_0,
                         m1 = model_1,
                         m2 = model_2))





```



### Lifecycle

This package is currently a *concept*, as defined by the [RECON software
lifecycle](https://www.reconverse.org/lifecycle.html). This means that
essential features and mechanisms are still being developed, and the
package is not ready for use outside of the development team.

### Contributions

Contributions are welcome via [pull
requests](https://github.com/TRACE-LAC/serofoi/pulls).

Contributors to the project include:

- [Zulma M. Cucunubá](https://github.com/zmcucunuba) (author)
- [Miguel Gamez](https://github.com/megamezl) (author)

### Code of Conduct

Please note that the linelist project is released with a [Contributor
Code of
Conduct](https://contributor-covenant.org/version/2/0/CODE_OF_CONDUCT.html).
By contributing to this project, you agree to abide by its terms.
