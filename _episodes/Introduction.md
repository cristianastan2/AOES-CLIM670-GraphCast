---
title: "Common Community Physics Package"
teaching: 0
exercises: 0
questions:
- "What is a Physics Package?"
objectives:
- "Learn about the Common Community Physics Package"
---
### Common Community Physics Package (CCPP) Ecosystem
- CCPP is designated to facilitate implementation of physics innovations in state-of-the-art atmospheric models, the use of various models to develop physics, and the acceleration of transition of physics innovations to operational models. 
- There are two distinct parts to the CCPP: 
  - a library of physical parameterizations (CCPP-Physics) that conforms to selected standards, and an infrastructure (CCPP-Framework) that enables connecting the physics to a host model. 
  - There is also a CCPP single-column model (CCPP SCM) which is a simplified framework that enables experimentation in a controlled setting using forcing datasets originating from experimental field campaigns.
 
![](https://dtcenter.org/sites/default/files/inline-images/CCPP%20Ecosystem%20Detailed.png)

- The CCPP aims to support the broad community while benefiting from the community. In such a CCPP ecosystem, the CCPP can be used not only by the operational centers to produce operational forecasts, but also by the research community to conduct investigation and development. Innovations created and effectively tested by the research community can be funneled back to the operational centers for further improvement of the operational forecasts.

### Common Community Physics Package (CCPP) System Architecture
- There are two distinct parts to the CCPP: a library of physical parameterizations (CCPP-Physics) that conforms to selected standards and an infrastructure (CCPP-Framework) that enables connecting the physics to a host model.

![](https://dtcenter.org/sites/default/files/inline-images/ccpp_arch_host_1.png)

- The host model needs to have functional documentation for any variable that will be passed to or received from the physics. The CCPP-framework is used to compare the variables requested by each physical parameterization against those provided by the host model, and to check whether they are available, otherwise an error will be issued. This process serves to expose the variables passed between physics and dynamics, and to clarify how information is exchanged among parameterizations. During runtime, the CCPP-Framework is responsible for communicating the necessary variables between the host model and the parameterizations.
