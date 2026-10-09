# Karachi Air Quality & Household Water Use

**Assignment 1: Exploratory Data Analysis, Data Wrangling & Inferential Statistics for Social Good**  
CS/SDP 312/314 L1 — Data Science for Social Good

This assignment explores environmental and household data from Karachi to understand pollution patterns, water consumption, and climate stress. It combines visual exploration, data preparation, statistical testing, and reflection on how analytical choices can affect public policy and resource allocation.

**Group 19:** Syed Muhammad Sameer Hassan (sh09036) and Yousuf Uyghur (07486).

## Read the assignment

- [Jupyter notebook](Assignment1_EDA_Statistics.ipynb) — code, charts, results, and written interpretations.
- [PDF report](Assignment1_EDA_Statistics.pdf) — included report for convenient reading.
- [Course assignment brief](Fall-Semester-2026-CS-SDP-312-314-L1-Data-Science-for-Social-Good.pdf).

## What the analysis covers

| Section | Topics |
| --- | --- |
| **A. Urban air toxicity** | Measurement scales, missing-data strategies, outlier detection with mean/SD and IQR, logarithmic transformations, and AQI discretization. |
| **B. Water consumption and climate stress** | Vertical concatenation, household and monthly aggregation, temperature–consumption correlation, and one-hot encoding. |
| **C. Inferential statistics** | Weekday/weekend comparisons, normality and variance diagnostics, Mann–Whitney U and t-tests, and a one-sample temperature test. |
| **D. Social impact and ethics** | Algorithmic bias, the “loop of neglect,” and the consequences of statistical choices for underserved households. |

## Data

All CSV files needed by the notebook are included in this repository.

| File | Contents |
| --- | --- |
| `air_quality_historical.csv` | 1,298 daily observations from August 1, 2022 to February 18, 2026, including pollutant concentrations, AQI, UV index, and dust. |
| `Water use data.csv` | 3,963 household-day observations from November 24, 2021 to July 10, 2023, covering 23 metered households, per-capita water use, maximum daily temperature, and calendar variables. |
| `city_info.csv` | Karachi geographic and city metadata. |
| `data_dictionary.csv` | Column descriptions and units for the air-quality and city files. |

In the water dataset, `NodeID` identifies a **metered household**, `wu_lpcd` is water use in **litres per capita per day**, and `maxDailyT` is maximum daily temperature in **degrees Fahrenheit**. The household sample should not be treated as representative of all Karachi residents.

## Selected findings

The following results are reported in the notebook:

- **Outlier rules change which pollution days are flagged.** The upper mean-plus-three-SD rule flags 28 PM2.5 days, while the upper IQR fence flags 65, illustrating how extreme values can inflate a non-resistant threshold.
- **Missing-data methods have little numerical impact here.** PM2.5 is missing on only 3 of 1,298 days; forward-fill cannot fill these leading gaps because no preceding reading exists.
- **Weekend water use is slightly lower.** Mean consumption is approximately 135.52 L/person/day on weekends versus 143.77 on weekdays. The reported effect is small (Cohen's d ≈ −0.075).
- **Observed temperatures exceed the assignment benchmark.** Mean maximum daily temperature is approximately 86.27°F compared with the 80°F benchmark.

These are descriptive and assignment-level inferential results. Repeated measurements within households, shared daily weather observations, uneven seasonal coverage, and observational data limit independence assumptions and causal interpretation. The notebook discusses these limitations alongside its policy interpretations.

## Run locally

The notebook was authored with **Python 3.12.3**. It uses pandas, NumPy, Matplotlib, seaborn, and SciPy.

1. Clone the repository and enter its directory:

   ```bash
   git clone https://github.com/Samzzh0803/DSFSG-A1.git
   cd DSFSG-A1
   ```

2. Install the analysis libraries and JupyterLab, preferably in a virtual environment:

   ```bash
   python -m pip install pandas numpy matplotlib seaborn scipy jupyterlab
   ```

3. Start JupyterLab from the repository directory:

   ```bash
   python -m jupyterlab
   ```

4. Open `Assignment1_EDA_Statistics.ipynb`, select a Python kernel, and run the cells from top to bottom. Keep the CSV files in the same directory as the notebook; its file paths are relative to that directory.

The repository does not pin dependency versions, so package updates may produce small differences in formatting or numerical output. The included PDF is a separate report artifact and is not regenerated automatically when the notebook changes.

## Dataset attribution

The notebook cites the following sources:

- Nitiraj, K., & Jagadish, T. (2026). *Air Quality Dataset for Karachi (2022-08-01 to 2026-02-18).* Zenodo. [Dataset DOI](https://doi.org/10.5281/zenodo.18673762).
- Khan, H. F. (2024). *Karachi household water use (daily resolution).* HydroShare. See the notebook's References section for the supplied resource link.
- Khan, H. F., Arif, M. A., Intikhab, S., & Arshad, S. A. (2023). *Quantifying Household Water Use and Its Determinants in Low-Income, Water-Scarce Households in Karachi.* Water, 15(19), 3400.

Consult the original sources for dataset methodology and reuse terms.
