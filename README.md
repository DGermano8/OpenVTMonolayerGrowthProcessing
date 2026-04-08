# OpenVT Monolayer Growth Processing

Post-processing and visualization notebooks for OpenVT monolayer growth simulation outputs.

This folder is used to:

- Load raw simulation outputs from Chaste and other frameworks.
- Compute summary geometry metrics (for example tissue area, perimeter, and roughness via concave hulls).
- Compare inhibition-related quantities (free surface fraction, free area fraction) across conditions.
- Generate publication-style figures and exploratory plots.

## Project Contents

- `Monolayer02Plot.ipynb`: Full plotting workflow for monolayer snapshots and parameter sweeps.
- `Monolayer02Plot_cleaning.ipynb`: Cleaned plotting and roughness-focused analysis.
- `Monolayer02Plot_dists.ipynb`: Radial/distribution analyses across simulation sets.
- `MonolayerTissueSize_cleaning.ipynb`: Tissue size and time-series processing, including roughness/area extraction.
- `data/`: Local data staging area, with multiple framework-specific subfolders.

## Python Requirements

The notebooks use Python with the following packages:

- `numpy`
- `matplotlib`
- `scipy`
- `shapely`
- `concave-hull`
- `jupyter`
- `ipympl` (for `%matplotlib widget` cells)



## Quick Start

1. Open this directory in VS Code.
2. Start with `Monolayer02Plot_cleaning.ipynb` for clearning data (Chaste specific).
3. Use `MonolayerTissueSize_cleaning.ipynb` for clearning data (Chaste specific).
4. Use `Monolayer02Plot_dists.ipynb` for radial and distribution views of the stacked no inhibition plots, for the 100, 1000 cell growth simulations.
5. Use `MonolayerTimeSeries_Plots.ipynb` for visualing the TimeSeries plots for the 100, 1000 cell growth simulations.
6. `Monolayer02Plot.ipynb` is my personal data viz playground.

