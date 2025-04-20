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
- Like traditional NWP systems, GraphCast is autoregressive: It can be “rolled out” by feeding its own predictions back in as input, to generate an arbitrarily long trajectory of weather states up to 10 days in advance.
![image](https://lh3.googleusercontent.com/PIGlxJLhF3Eit7xSXvVPmm3ZnOYspa9a8RcRkzfEdSnhy2rVubJmIondGQGiKF3TbHTIUOi6w_8xAej5UJ--c7o_8OukH_bDi4gYuEaQ0N6d_BXRQw=w2140-rw)

### GraphCast Architecture

- Consists of Graph Neural Networks (GNNs) - one of teh fastest growing class of machine learning models in an "encoder-processor-decoder" configuration (Fig. 1D-F) in [Lam et al. 2023](https://www-science-org.mutex.gmu.edu/doi/10.1126/science.adi2336).
- Uses 36.7 million parameters
- In the encoder, the input variables are normalized to zero mean and unit variance and uses a single GNN layer.
- It has an internal multimesh representation defined by refining a regular icosahedron (12 nodes, 20 faces, 30 edges) iteratively six times. The multimesh contains 40,962 nodes
- The processor uses 16 unshared GNNs layers to perform learned message-passing steps, enabling efficient local and long-range information propagation.
- The decoder uses a single GNN layer to map the final processor layer's learned features from the multimesh representtaion back to the latitude-longitude grid.
  
### Training
- It was trained using 39 years (1979-2017) data from ERA5 reanalysis.
  
### Verification
[![YouTube video player](https://www.youtube.com/watch?v=Q6fOlW-Y_Ss)](https://www.youtube.com/embed/Q6fOlW-Y_Ss?si=KVNyjxjMfjQE5muJ
