# Approximate Bayesian Computation for Disease OutbreakABC for Influenza Epidemic Models

![Project Logo](logo_abc.png) 

## Overview

This project applies Approximate Bayesian Computation (ABC) to fit parameters in a model for influenza A and B strains, using data from past outbreaks in Michigan and Seattle. The goal is to replicate the model selection results from the paper "[Simulation-based model selection for dynamical systems in systems and population biology](https://watermark.silverchair.com/bioinformatics_26_1_104.pdf?token=AQECAHi208BE49Ooan9kkhW_Ercy7Dm3ZL_9Cf3qfKAc485ysgAAA3swggN3BgkqhkiG9w0BBwagggNoMIIDZAIBADCCA10GCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQMjV15kHzFknWstbVZAgEQgIIDLvGZcFAgMxJ2FtxTGrsPvkAoO-imsFvwyY2RJRbPWpz_WYOR3ZYIIXnJpmCp_pOOlhB9fGwvPCCBNkFN7jjQvo-jtSs3vYGT9U9ABO1ngcGxGq0M_-xfz5QDNcfLJpdHphXjvXPmNQKw-FbmW7Z-lM4VADhWgRMXeAa69IcQWbf3O3M4YVlAfOhNibTRLt8QLpayutZlbZAwX6aC2a13wmjnKF6Vx3WJWazbewssqJov9CmNXprFKUqnhcq1QLZ4oaGSKYaxVFpmwB2ZylzUBbliQ3fYN6VRAfleLXrmyvOymid2GtXNnhrslyx6SN2OSgbXU0YIgfSgCk5OaCETsFY7VMGzLCuUTB776n6hDJKcZ-Hb7RelIJxLeOZteaxRVOiu-a9pG5NbQQuueQtS0C-kqHlVksEwUAucqzS9UXX3ucvmsIgYK-jQQ8jmtqPTjVkdFGhR1J3LzOw7VJCJQy4b_a_WZLDNS7bskxvvZgU7DOZAVHxYu1aPUHh3UaeJ-5oMwJ-sqFWg_6ZruUPk4L9f1KB1siRgSmxw-Eo4JHKXjSEsIXAylD3m_trgxEIxkeqgXFJ867U-qJxeG39ToS9BptAG_IGK-HfMD0ovPK9mKHXvrp32fRO5S0oiqaCMa8kV4DGwbZjaMArJDV9Ps3WNw_EE2E8m7J4UjiqLNQkihUtUM6d4xmJ-S4zo-qPJkr0ajWkDhQwkeJ1wsaYGXItivcoAB4lzyQmG3Zs5kQQIIa2m4hveEf2mDlglHMoPHTAN5hGG-9_LegexhFcKAZTguF4nNpozqAVsIQaj8DeAaHWY8AvjP5HjDTgYHs4ni3w7EjULGDSroFhBndTpCAMNjtY9yIqoh248Bf7ayWtBCXUx1yJyIamAPGeHej3nPnf80TACr2Of6fJicQ-hFcdVGzQj8qiq8b9GuOFFJ43SnZudftdAwwlA0mQb30ZhvgJvsYngGY752-NegVEd2F_r6N2Jkw-G-fzEnoObf6OXzGaYlNSq4_s4vGnQ38HGe_HPk7fdDIESUA35j1SbK5K83274IWvReND0Byubb2MmgZ4fJ90sCCKnjLeu9ho)", and demonstrate how ABC can be used to estimate model parameters for complex epidemic models.

---

## Objectives

The primary objectives of this project are:

- Replicate the model selection results in [Tony and Stumpf's paper](https://watermark.silverchair.com/bioinformatics_26_1_104.pdf?token=AQECAHi208BE49Ooan9kkhW_Ercy7Dm3ZL_9Cf3qfKAc485ysgAAA3swggN3BgkqhkiG9w0BBwagggNoMIIDZAIBADCCA10GCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQMjV15kHzFknWstbVZAgEQgIIDLvGZcFAgMxJ2FtxTGrsPvkAoO-imsFvwyY2RJRbPWpz_WYOR3ZYIIXnJpmCp_pOOlhB9fGwvPCCBNkFN7jjQvo-jtSs3vYGT9U9ABO1ngcGxGq0M_-xfz5QDNcfLJpdHphXjvXPmNQKw-FbmW7Z-lM4VADhWgRMXeAa69IcQWbf3O3M4YVlAfOhNibTRLt8QLpayutZlbZAwX6aC2a13wmjnKF6Vx3WJWazbewssqJov9CmNXprFKUqnhcq1QLZ4oaGSKYaxVFpmwB2ZylzUBbliQ3fYN6VRAfleLXrmyvOymid2GtXNnhrslyx6SN2OSgbXU0YIgfSgCk5OaCETsFY7VMGzLCuUTB776n6hDJKcZ-Hb7RelIJxLeOZteaxRVOiu-a9pG5NbQQuueQtS0C-kqHlVksEwUAucqzS9UXX3ucvmsIgYK-jQQ8jmtqPTjVkdFGhR1J3LzOw7VJCJQy4b_a_WZLDNS7bskxvvZgU7DOZAVHxYu1aPUHh3UaeJ-5oMwJ-sqFWg_6ZruUPk4L9f1KB1siRgSmxw-Eo4JHKXjSEsIXAylD3m_trgxEIxkeqgXFJ867U-qJxeG39ToS9BptAG_IGK-HfMD0ovPK9mKHXvrp32fRO5S0oiqaCMa8kV4DGwbZjaMArJDV9Ps3WNw_EE2E8m7J4UjiqLNQkihUtUM6d4xmJ-S4zo-qPJkr0ajWkDhQwkeJ1wsaYGXItivcoAB4lzyQmG3Zs5kQQIIa2m4hveEf2mDlglHMoPHTAN5hGG-9_LegexhFcKAZTguF4nNpozqAVsIQaj8DeAaHWY8AvjP5HjDTgYHs4ni3w7EjULGDSroFhBndTpCAMNjtY9yIqoh248Bf7ayWtBCXUx1yJyIamAPGeHej3nPnf80TACr2Of6fJicQ-hFcdVGzQj8qiq8b9GuOFFJ43SnZudftdAwwlA0mQb30ZhvgJvsYngGY752-NegVEd2F_r6N2Jkw-G-fzEnoObf6OXzGaYlNSq4_s4vGnQ38HGe_HPk7fdDIESUA35j1SbK5K83274IWvReND0Byubb2MmgZ4fJ90sCCKnjLeu9ho), using a 4-parameter model and observed data from **Table 2** (Addy et al., 1991) and **Table 3** (Longini and Koopman, 1982) from the [Supplementary Data](https://academic.oup.com/bioinformatics/article/26/1/104/182571).

---

## Methodology

### Generating ABC Samples

The ABC algorithm is applied to fit the parameters of the 4-parameter model:

1. **Parameters**: $(q_{c1}, q_{h1}, q_{c2}, q_{h2})$.
2. **Prior**: Uniform distribution for the parameters: $P(q) \sim \text{Uniform}[0, 1]$.
3. **Model**: Simulate data based on $P(D_{obs}|q) \sim w_{js}$.
4. **Similarity Measure**: $d(D_{obs}, D^*) = \frac{1}{2} \left( \| D_1 - D^*(q_{c1}, q_{h1}) \|_F + \| D_2 - D^*(q_{c2}, q_{h2}) \|_F \right)$.
5. **Acceptance Criteria**: If $d(D_{obs}, D^{*(i)}) < \epsilon$, accept $q^{(i)}$.

#### Sampling Procedure
For $i = 1, 2, \dots, N$:
- Generate $q^{(i)} \sim \text{Uniform}[0,1]$
- Generate $D^{*(i)} \sim w_{js}$

The accepted parameter values approximate the posterior distribution $P(q|D_{obs})$.

### Model Comparison using ABC

- **Input**: A set of models to compare: $m^{(i)} \in M$.
- **Prior**: $P(m)$ for models and $P(q | m)$ for parameters.
- **Simulation**: Generate $D^{*(i)} \sim f(q^{(i)} | m^{(i)})$.
- **Acceptance Criterion**: If $d(D_{obs}, D^{*(i)}) < \epsilon$, accept $q^{(i)}$.

The model posterior probability is approximated by the ratio of accepted samples:
$$P(m^{(i)}|D_{obs}) \approx \frac{\text{\# accepted samples for } m^{(i)}}{\text{\# total accepted samples}}$$

---

## Conclusion

By applying ABC to model influenza outbreaks, we show that the 4-parameter model performs well in distinguishing parameters for different outbreaks. Furthermore, using the ABC rejection sampler for model comparison, we conclude that outbreaks of the same strain of influenza are best modeled by a 2-parameter model, whereas outbreaks of different strains are better modeled by a 3-parameter model.

   git clone https://github.com/yourusername/abc-influenza-model.git
