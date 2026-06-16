---
layout: post
author: "Yeji Kim"
title:  "Digital Twin Framework for Remote Water Distribution Systems"
subtitle: "End-to-end monitoring and decision-support platform deployed in Unalakleet, Alaska"
type: "Published"
projects: true
text: true
ridi: true
portfolio: true
header-img: "img/wds_dt.png"
main-img: "img/wds_dt.png"
role-title: "First Author"
role-specific: 
team: "Yeji Kim, Yifan Huang, Rebecca Cantrell, Matthew Bartos, Lina Sela"
platforms: "Python (WNTR, EPANET, epanet-js), Flask, AWS EC2, InfluxDB, Plotly, Leaflet"
date: "Jan 2024 – Jun 2026"
order: 9
---

**Published:** *<b>Kim, Y.</b>, Huang, Y., Cantrell, R., Bartos, M., & Sela, L. (2026). ACS ES&T Water, 6, 3543–3554.* [DOI →](https://pubs.acs.org/doi/10.1021/acsestwater.5c01515)

**Live Dashboard:** [Unalakleet WDS Digital Twin →](http://ec2-34-235-111-72.compute-1.amazonaws.com:5000/)

![Digital Twin Workflow](img/wds_dt.png)

# Overview

Water distribution systems (WDSs) in **remote communities** often operate with limited staffing, aging infrastructure, and few digital tools. This work develops an **end-to-end digital twin framework** for resource-constrained utilities and demonstrates its implementation in the WDS of **Unalakleet, Alaska** — a community of ~800 residents in the Norton Sound region.

# Approach

- **Designed and deployed** a custom wireless sensor network (pressure + temperature) on four distribution loops, with solar-powered cellular nodes feeding **AWS EC2 / InfluxDB**
- Built a **dynamic hydraulic model** (EPANET / WNTR / epanet-js) integrating sensor data, ANTHC SCADA flows, and tank levels for continuous state estimation
- Developed a **browser-based dashboard** (Flask + Plotly + Leaflet) for operator-facing visualization and decision support

# Key Results

The digital twin reconstructs the hydraulic state with high fidelity:

| Variable | CRPS |
|---|---|
| System pressure head | **0.065 m** |
| Tank level | **0.022 m** |
| Loop pressures | 0.198 – 0.393 m |

![Validation results](img/wds_estimation.png)

Validated use cases:
- **Anomaly detection** — diagnosed a pressure-drop event in June 2025
- **Maintenance outage support** — risk-free testing of planned shutdowns
- **Fire-flow capacity assessment** — system-wide stress testing for infrastructure planning

# Reference

**Kim, Y.**, Huang, Y., Cantrell, R., Bartos, M., & Sela, L. (2026). *From Field Data to Smart Operations: A Digital Twin Framework for Water Distribution Systems in Remote Communities.* **ACS ES&T Water**, 6, 3543–3554. [https://doi.org/10.1021/acsestwater.5c01515](https://pubs.acs.org/doi/10.1021/acsestwater.5c01515)
