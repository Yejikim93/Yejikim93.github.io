---
layout: post
author: "Yeji Kim"
title:  "Probabilistic Leak Detection in Water Distribution Networks"
subtitle: "Bayesian framework for leak detection and localization under hydraulic uncertainty"
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
platforms: "Python, EPANET, AWS data pipeline, Bayesian inference"
date: "Jan 2024 – Dec 2025"
order: 10
---

**Status:** Manuscript in preparation — *<b>Kim, Y.</b> & Bartos, M. (2026). Probabilistic parameter-estimation framework for discovery of pre-existing leaks in water distribution systems* (target: **Water Research**).

![WDS testbed](img/project9_WDS_testbed.png)

# Overview

This work develops a **probabilistic framework** for **leak detection, localization, and system diagnostics** in water distribution networks operating under uncertainty in pipe roughness, demand variability, and hydraulic losses. The framework is validated on a pilot-scale water distribution network in **Unalakleet, Alaska** (4 loops, ~740 population).

# Approach

- **Python-based hydraulic modeling and data assimilation** using EPANET for network-wide state estimation
- **Bayesian inference** for leak detection and localization, propagating uncertainty in model parameters and field conditions
- **SCADA API integration** with wireless pressure sensors and adaptive sampling, on an AWS-based data pipeline
- Decision-support tools for **pump scheduling and valve control** validated against pilot deployment data

# Expected Contributions

- Continuous monitoring and anomaly detection under realistic operating uncertainty
- Quantitative leak localization with confidence bounds
- Data-driven operational decisions for utility operators in resource-constrained networks
