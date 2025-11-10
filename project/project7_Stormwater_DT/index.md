---
layout: post
author: "Yeji Kim"
title:  "Stormwater Digital twin "
subtitle: "Stormwater digital twin with online quality control detects urban flood hazards under uncertainty"
type: "Compeleted"
projects: true
text: true
ridi: true
portfolio: true
post-header: true
header-img: "img/project7_Stormwater_DT.png"
main-img: "img/project7_Stormwater_DT.png"
role-title: "First Author"
role-specific: 
team: "Yeji Kim, Jeil Oh, Matthew Bartos"
platforms: ""
date: "Jun 2022- Dec 2023"
order: 8
---

# Stormwater Digital twin 
## Stormwater digital twin with online quality control detects urban flood hazards under uncertainty
![project7_Stormwater_DT](img/project7_Stormwater_DT.png)
# Abstract 
Urban drainage systems face increased floods and combined sewer overflows due to climate change and population growth. To manage these hazards, cities are seeking stormwater digital twins that integrate sensor data with hydraulic models for real-time response. However, these efforts are complicated by unreliable sensor data, imperfect hydrologic models, and inaccurate rainfall forecasts. To address these issues, we introduce a stormwater digital twin system that uses online data assimilation to estimate stormwater depths and discharges under sensor and model uncertainty. We first derive a novel state estimation scheme based on Extended Kalman Filtering that fuses sensor data into a hydraulic model while simultaneously detecting and removing faulty measurements. The system’s accuracy is evaluated through a long-term deployment in Austin’s flood-prone Waller Creek watershed. The digital twin model demonstrates enhanced accuracy in estimating stormwater depths at ungauged locations and delivers more accurate near-term forecasts. Moreover, it effectively identifies and removes sensor faults from streaming data, achieving a Receiver Operating Characteristic Area Under the Curve (ROC AUC) of over 0.99 and significantly reducing the potential for false flood alarms. This study provides a complete software implementation, offering water managers a reliable framework for real-time monitoring, rapid flood response, predictive maintenance, and active control of sewer systems.

# Results

The digital twin model excels in both rejecting sensor faults and improving stormwater model accuracy. Here, the digital twin model refers to the hydraulic-hydrologic model with data assimilation, while the base model refers to the same model without data assimilation. First, while the raw sensor data exhibits multiple faults that would otherwise register as false alarms, the digital twin model filters these outliers, producing continuous estimates of the water depth in the creek. Moreover, while the base model tends to overpredict peak depths, the digital twin model rejects these overestimates by incorporating the depth sensor data into the final estimate. In general, the digital twin output mediates between the model estimates and sensor measurements, producing an output that is consistent with both data sources. 
![project7_Stormwater_DT](img/project7_Stormwater_DT_results.png)
# Reference

[https://www.sciencedirect.com/science/article/pii/S2210670724008060](https://www.sciencedirect.com/science/article/pii/S2210670724008060)
