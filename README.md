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

Install in a virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install numpy matplotlib scipy shapely concave-hull jupyter ipympl
```

## Data Expectations

These notebooks expect simulation outputs to already exist and be exported as text/CSV files.

Observed patterns in the notebooks include:

- Chaste output roots in `chaste_output/.../results_from_time_0/`.
- CSV batches in folders like:
	- `data/1000_Data/...`
	- `data/1000_Data_Slower/...`
	- `data/timeSeries/...`
	- `data/timeseries_1K_PhysiCell/...`

Typical file names consumed by the analysis:

- `celldata_Radius.dat`
- `celldata_FreeSurfaceFraction.dat`
- `celldata_FreeAreaFraction.dat`
- `celldata_growth inhibited.dat`
- `cell_data_no_inhibition_<index>.csv`
- `data<index>.csv`

## Quick Start

1. Open this directory in VS Code.
2. Select a Python kernel that has the required packages installed.
3. Start with `Monolayer02Plot_cleaning.ipynb` for snapshot/roughness figures.
4. Use `MonolayerTissueSize_cleaning.ipynb` for time-series/tissue-size processing.
5. Use `Monolayer02Plot_dists.ipynb` for radial and distribution views.

## Important Notes

- Some notebook cells contain machine-specific absolute paths (for example under `/Users/.../ChasteWorkspace/chaste_output/`). Update these paths to match your local filesystem before running.
- Several workflows assume a specific naming convention for simulation folders and indexes. Keep directory/file names consistent with the expected patterns above.
- If a cell errors with "file not found", verify both:
	- The root dataset folder is correct.
	- The per-simulation file naming format matches the selected framework (for example zero-padded vs non-padded indexes).

## Troubleshooting

- `ModuleNotFoundError: concave_hull`:
	- Install `concave-hull` into the active kernel environment.
- `FileNotFoundError` for `dataXXXXXX.csv` or `cell_data_no_inhibition_*.csv`:
	- Confirm the expected folder exists and file numbering scheme matches the notebook logic.
- Empty or NaN-heavy plots:
	- Check delimiter assumptions (comma vs tab) and whether headers/columns match expected layout.

## Output

Outputs are generated directly in notebook cells and, in some workflows, saved as PNG figures into local data/result folders.

If you add new workflows, keep notebook names descriptive and document any new data layout assumptions in this README.
