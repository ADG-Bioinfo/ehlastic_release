[![DOI](https://zenodo.org/badge/1378733934.svg)](https://doi.org/10.5281/zenodo.22974488)

# EHLAstic Release

This repository contains the release package for the EHLAstic HLA-E analysis notebooks and figure-generation workflow.

The `notebook/` directory currently contains four primary notebooks:

- `fig_model.ipynb`
- `fig_jurkat.ipynb`
- `fig_location.ipynb`
- `fig_aml_all_pbmc.ipynb`

Generated figures are written under `figure/`, and the required input datasets are expected under `data/`.

The `data/` directory is not intended as a public redistribution bundle and will be made available upon request.

## Requirements

- Windows PowerShell or another shell capable of activating a Python virtual environment
- Python `>=3.11,<3.12`
- `uv` for environment management and dependency installation

## Python Dependencies

The project metadata in `pyproject.toml` is the source of truth. The notebook environment depends on:

- `numpy==1.26.3`
- `pandas==2.1.4`
- `scikit-learn==1.3.2`
- `openpyxl>=3.1.5`
- `matplotlib>=3.10.7`
- `seaborn>=0.13.2`
- `jupyterlab>=4.5.0`

## Setup with `uv`

The recommended setup is a local `.venv` managed by `uv`.

### 1. Install `uv`

If `uv` is not already installed, install it in PowerShell:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

After installation, restart the shell so the `uv` command is available.

### 2. Create the virtual environment

From the repository root:

```powershell
cd D:\Projects\ehlastic_release
uv venv --python 3.11 .venv
```

### 3. Activate the virtual environment

```powershell
.\.venv\Scripts\Activate.ps1
```

If PowerShell blocks activation, run:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
```

and then activate `.venv` again.

### 4. Install the project dependencies

```powershell
uv sync
```

This installs the dependencies declared in `pyproject.toml` into `.venv`.

## Launch JupyterLab

With the environment active, start JupyterLab from the repository root:

```powershell
uv run jupyter lab
```

Then open any of the notebooks in `notebook/` and run the cells sequentially.

## Repository Layout

- `notebook/`: notebook workflows for model, Jurkat, peptide-location, and AML/ALL/PBMC figures
- `data/`: required input data, including `IEDB`, `IMGT_HLA`, `Max_Gerry`, `Protein_Database`, and location tables
- `figure/`: rendered figure outputs grouped by figure panel

## Notes

- Several notebooks hardcode `project_dir` and derive paths relative to `D:/Projects/ehlastic_release`. Update that variable to the project root directory.

- The notebooks assume the repository is fully populated with the provided `data/` subdirectories; they are not standalone examples with synthetic input.

- The `data/` contents will be made available upon request.

