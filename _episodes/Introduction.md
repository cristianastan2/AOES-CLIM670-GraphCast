---
title: "GraphCast Machine Learning based weather prediction"
teaching: 0
exercises: 0
questions:
- "What is GraphCast?"
objectives:
- "Learn about an machine learning weather prediction (MLWP) approach for global medium-range weather forecasting"
---
### GraphCast
- The material presented here is adopted from the [Google Deep Mind](https://deepmind.google/discover/blog/graphcast-ai-model-for-faster-and-more-accurate-global-weather-forecasting/) and [Science paper](https://www.science.org/stoken/author-tokens/ST-1550/full).
- AI model able to make medium-range weather forecasts up to 10 days in advance
- Much faster than the industry gold-standard weather simulation
 
![](https://dtcenter.org/sites/default/files/inline-images/CCPP%20Ecosystem%20Detailed.png)

- The CCPP aims to support the broad community while benefiting from the community. In such a CCPP ecosystem, the CCPP can be used not only by the operational centers to produce operational forecasts, but also by the research community to conduct investigation and development. Innovations created and effectively tested by the research community can be funneled back to the operational centers for further improvement of the operational forecasts.

### Common Community Physics Package (CCPP) System Architecture
- There are two distinct parts to the CCPP: a library of physical parameterizations (CCPP-Physics) that conforms to selected standards and an infrastructure (CCPP-Framework) that enables connecting the physics to a host model.

![](https://dtcenter.org/sites/default/files/inline-images/ccpp_arch_host_1.png)

- The host model needs to have functional documentation for any variable that will be passed to or received from the physics. The CCPP-framework is used to compare the variables requested by each physical parameterization against those provided by the host model, and to check whether they are available, otherwise an error will be issued. This process serves to expose the variables passed between physics and dynamics, and to clarify how information is exchanged among parameterizations. During runtime, the CCPP-Framework is responsible for communicating the necessary variables between the host model and the parameterizations.
