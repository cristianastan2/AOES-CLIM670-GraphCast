---
title: "GraphCast Machine Learning based weather prediction"
teaching: 0
exercises: 0
questions:
- "What is GraphCast?"
objectives:
- "Learn about an machine learning weather prediction (MLWP) approach for global medium-range weather forecasting"
---
### GraphCast Overview
- The material presented here is adopted from the [Google Deep Mind](https://deepmind.google/discover/blog/graphcast-ai-model-for-faster-and-more-accurate-global-weather-forecasting/) and [Science paper](https://www-science-org.mutex.gmu.edu/doi/10.1126/science.adi2336).
- AI model able to make medium-range weather forecasts up to 10 days in advance
- Much faster than the industry gold-standard weather simulation system - the Ensemble Control forecast system ([ex-HRES](https://confluence.ecmwf.int/display/FUG/Section+2.1.2+Model+Configurations)), produced by the European Center for Medium-range Weather Forecast (ECMWF).
- GraphCast can also offer earlier warnings of extreme weather events. It can predict the tracks of cyclones with great accuracy further into the future, identifies atmospheric rivers associated with flood risk, and predicts the onset of extreme temperatures. This ability has the potential to save lives through greater preparedness.

### Graphcast Description
- Takes as input the two most recent states of Earth’s weather—the current time and 6 hours earlier—and predicts the next state of the weather 6 hours ahead. - A single weather state is represented by a 0.25° latitude-longitude grid (721 by 1440), which corresponds to roughly 28 km by 28 km resolution at the equator.
- Each grid point represents a set of surface and atmospheric variables (listed in Table 1).
- Like traditional NWP systems, GraphCast is autoregressive: It can be “rolled out” by feeding its own predictions back in as input, to generate an arbitrarily long trajectory of weather states.

![](https://www-science-org.mutex.gmu.edu/cms/10.1126/science.adi2336/asset/c93512fe-4811-4edf-aa57-376c670c31b3/assets/images/large/science.adi2336-f1.jpg)
