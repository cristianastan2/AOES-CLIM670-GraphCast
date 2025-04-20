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
- The material presented here is adopted from the [Google Deep Mind](https://deepmind.google/discover/blog/graphcast-ai-model-for-faster-and-more-accurate-global-weather-forecasting/) and [Lam et al. 2023](https://www-science-org.mutex.gmu.edu/doi/10.1126/science.adi2336).
- AI model able to make medium-range weather forecasts up to 10 days in advance
- Much faster than the industry gold-standard weather simulation system - the Ensemble Control forecast system ([ex-HRES](https://confluence.ecmwf.int/display/FUG/Section+2.1.2+Model+Configurations)), produced by the European Center for Medium-range Weather Forecast (ECMWF).
- GraphCast can also offer earlier warnings of extreme weather events. It can predict the tracks of cyclones with great accuracy further into the future, identifies atmospheric rivers associated with flood risk, and predicts the onset of extreme temperatures. This ability has the potential to save lives through greater preparedness.

### Graphcast Description
- Takes as input the two most recent states of Earth’s weather—the current time and 6 hours earlier—and predicts the next state of the weather 6 hours ahead. - A single weather state is represented by a 0.25° latitude-longitude grid (721 by 1440), which corresponds to roughly 28 km by 28 km resolution at the equator.
- Each grid point represents a set of surface variable and atmospheric variables at 37 levels:
  * 2-meter Temperature (2T)
  * 10-meter zonal wind component (10U)
  * 10-meter meridional wind component (10V)
  * Mean sea level pressure (MSL)
  * Total precipitation (TP)
  * Temperature (T)
  * Zonal wind component (U)
  * Meridional wind component (V)
  * Geopotential (Z)
  * Specific humidity (Q)
  * Vertical wind speed (W)
- Like traditional NWP systems, GraphCast is autoregressive: It can be “rolled out” by feeding its own predictions back in as input, to generate an arbitrarily long trajectory of weather states (Fig. 1A).

### GraphCast Architecture

![](https://www-science-org.mutex.gmu.edu/cms/10.1126/science.adi2336/asset/c93512fe-4811-4edf-aa57-376c670c31b3/assets/images/large/science.adi2336-f1.jpg)
(A) The input weather state(s) are defined on a 0.25° latitude-longitude grid comprising a total of 721 × 1440 = 1,038,240 points. Yellow layers in the close-up pop-out window represent the five surface variables, and blue layers represent the six atmospheric variables that are repeated at 37 pressure levels (5 + 6 × 37 = 227 variables per point in total), resulting in a state representation of 235,680,480 values. (B) GraphCast predicts the next state of the weather on the grid. (C) A forecast is made by iteratively applying GraphCast (GC) to each previous predicted state, to produce a sequence of states that represent the weather at successive lead times. (D) The encoder component of the GraphCast architecture maps local regions of the input (green boxes) into nodes of the multimesh graph representation (green, upward arrows that terminate in the green-blue node). (E) The processor component updates each multimesh node using learned message-passing (heavy blue arrows that terminate at a node). (F) The decoder component maps the processed multimesh features (purple nodes) back onto the grid representation (red, downward arrows that terminate at a red box). (G) The multimesh is derived from icosahedral meshes of increasing resolution, from the base mesh (M0, 12 nodes) to the finest resolution (M6, 40,962 nodes), which has uniform resolution across the globe. It contains the set of nodes from M6 and all the edges from M0 to M6. The learned message-passing over the different meshes’ edges happens simultaneously, so that each node is updated by all of its incoming edges. [The Earth texture in the figure is used under CC BY 4.0 from https://www.solarsystemscope.com/textures/]. From [Lam et al. 2023](https://www-science-org.mutex.gmu.edu/doi/10.1126/science.adi2336)

- Consists of Graph Neural Networks (GNNs) - one of teh fastest growing class of machine learning models in an "encoder-processor-decoder" configuration (Fig. 1D-F).
- 
-  
