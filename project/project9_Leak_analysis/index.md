---
layout: post
author: "Yeji Kim"
title:  "Leak Detection and Localization in Water Distribution Networks"
subtitle: "One pipeline, two analyses: ensemble hydraulic models calibrated by population Monte Carlo, with the leak inferred by marginalization over the calibrated ensemble"
type: "In Preparation"
projects: true
text: true
ridi: true
portfolio: true
header-img: "img/project9_WDS_testbed.png"
main-img: "img/project9_WDS_testbed.png"
role-title: "First Author"
role-specific: 
team: "Yeji Kim, Matthew Bartos"
platforms: "Python, pipedream, EPANET / WNTR, Population Monte Carlo, Bayesian inference, AWS data pipeline"
date: "Jan 2024 – Present"
order: 10
---

<style>
.post table { border-collapse: collapse; width: 100%; margin: 24px 0; font-size: 15px; line-height: 1.6; }
.post th, .post td { border-top: 1px solid #e2e2e2; padding: 12px 14px; vertical-align: top; text-align: left; }
.post thead th { border-top: none; border-bottom: 2px solid #333; font-weight: 700; }
.post tbody tr td:first-child { white-space: nowrap; color: #666; }
.post code { background: #f4f4f4; padding: 2px 6px; border-radius: 3px; font-size: 14px; }
.post img.figure-full { max-width: 100%; width: 100%; margin: 32px 0; }
</style>

Model-based leak detection and localization compares measured pressure with model-predicted pressure. Parametric error in roughness, base demand, pump curve, and minor losses typically exceeds the leak-induced head change, so the residual is dominated by model error rather than by the leak. Conventional practice is to calibrate a few coefficients by hand. This framework replaces that step with ensemble calibration and marginalization.

Detection, size estimation, and localization are not stages of a workflow. They are the same pipeline instantiated on a different inference target: the prior, the calibrated ensemble, and the marginalization step are shared, and only the likelihood and the decision rule change.

<img class="figure-full" src="img/project9_method_framework.png" alt="Five stages: priors on the uncertain parameters, an ensemble refined by population Monte Carlo, a likelihood under each draw, marginalization over the ensemble, and a decision rule. The two rows are the two analyses, sharing every stage but the likelihood and the decision." />

# The shared pipeline

**Prior.** θ collects roughness, base demand, pump curve, and minor losses, plus the leak parameters of whichever analysis is running. Priors are broad and independent.

**Ensemble.** *N* draws θ<sub>*d*</sub> from the prior. Each draw simulates the baseline and every leak scenario under the same θ<sub>*d*</sub>, so a leak signature and its baseline carry a common model error that differencing removes.

**Population Monte Carlo.** Importance weights against pressure sensors and the metered system inflow, followed by resampling and jitter, with the posterior serving as the next proposal:

<p><code>w<sub>d</sub> &prop; p(D &#124; &theta;<sub>d</sub>) p(&theta;<sub>d</sub>) / q(&theta;<sub>d</sub>)</code></p>

Leak flow meters are never read; the leak flow enters as a parameter to be estimated.

**Marginalization.** The target is averaged over the calibrated ensemble rather than evaluated at a point estimate:

<p><code>p(x &#124; y) = (1/N) &Sigma;<sub>d</sub> p(x &#124; y, &theta;<sub>d</sub>)</code></p>

Hydraulics are solved with [pipedream](https://github.com/mdbartos/pipedream), which integrates the Saint-Venant equations with a Preissmann slot for pressurized flow.

# The two instantiations

|  | Detection and size | Localization |
|---|---|---|
| Target *x* | leak area *a* | candidate junction *c* |
| Observations | pump flow and pressure, as a time series | tap pressures and the metered system inflow |
| Likelihood | kernel density estimate over the ensemble samples of leak area, pressure, and flow, conditioned on the observation at each time step and accumulated across the series<br><code>f&#770;(a,H,Q) = (1/N) &Sigma;<sub>i</sub> K<sub>h</sub>( &middot; &minus; (a<sub>i</sub>,H<sub>i</sub>,Q<sub>i</sub>) )</code> | a fingerprint catalogue per draw, the head change at the taps for a leak at each candidate; common mode removed and a leak scale fitted per candidate, so only shape is compared, leaving a residual *r*<sub>*c*</sub> in units of sensor noise<br><code>p(c &#124; y, &theta;) &prop; exp( &minus;r<sub>c</sub> / 2&sigma;<sup>2</sup> )</code> |
| Decision | Bayes factor on the Kass-Raftery scale, a leak declared at BF<sub>10</sub> &gt; 10; size as the MAP or median with a credible interval<br><code>BF<sub>10</sub> = p(y &#124; M<sub>1</sub>) / p(y &#124; M<sub>0</sub>)</code> | every candidate above a cost-ratio threshold is reported, with *C* the cost of a crew visit and *W* the cost of a missed leak; the posterior also yields a credible set over junctions<br><code>&tau; = C / (W + C)</code> |
| PMC schedule | five trials after marginalization; real-time detection skips the loop and runs on the prior ensemble | once on a design period, before the catalogue is built; parameters, thresholds, and ensemble are then fixed |

# References

- **Kim, Y.** & Bartos, M. *Probabilistic parameter-estimation framework for discovery of pre-existing leaks in water distribution systems.* In preparation (target: Water Research).
- **Kim, Y.** & Bartos, M. (2026). *Uncertainty-Aware Leak Detection and Localization in Water Distribution Networks.* Poster, WEFTEC 2026.

Supported by the National Science Foundation under Grant 2220516.
