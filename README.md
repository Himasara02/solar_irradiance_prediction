# Solar Irradiance Validation & Analysis Toolkit ☀️🇱🇰

## 📋 Project Overview
This project provides a comprehensive data analysis pipeline to evaluate the accuracy of satellite-based solar irradiance data (**CAMS** and **Solcast**) against real-world **Ground Sensor** data in Sri Lanka. 

Designed to support decision-making for commercial solar power plants, this repository contains tools for fetching, cleaning, aligning, and visualizing solar data across multiple tropical locations (Kebithigollawa, Gampaha, Kandy, etc.).

## 🚀 Key Features

### 1. Multi-Source Data Integration
- **Ground Truth:** Processing logic for high-resolution sensor data (1-min intervals).
- **CAMS API:** Automated scripts to fetch data from the Copernicus Atmosphere Monitoring Service (ADS) using `cdsapi`.
- **Solcast API:** Integration and cleaning of Solcast historical time-series data.
- **OpenMeteo:** Comparative analysis with OpenMeteo solar data.

### 2. Advanced Data Processing
- **Kalman Filtering:** Implementation of a 1D Kalman Filter to denoise raw sensor data and extract the "true" solar trend from noisy readings.
- **Time Alignment:** Algorithms to synchronize disparate timezones (UTC vs. Local) and time definitions (Period Start vs. Period End).
- **Unit Conversion:** Auto-conversion between Energy ($Wh/m^2$) and Power ($W/m^2$).

### 3. Interactive Visualizations
- **Daily & Monthly Scatters:** Interactive Plotly dashboards to compare daily average irradiance across multiple sites.
- **Zoomable Time-Series:** High-resolution comparison plots to visualize cloud-passing events ("spikes") vs. satellite smoothing.
- **Correlation Analysis:** Statistical validation of satellite models against ground truth.

## 🛠️ Technologies Used
* **Python 3.x**
* **Pandas** (Time-series manipulation)
* **Plotly** (Interactive dashboards)
* **Matplotlib** (Static plotting)
* **CDS API** (Copernicus data access)
* **NumPy / SciPy** (Kalman filtering & math)

## 📊 Key Findings
* **CAMS (European Satellite):** Excellent for long-term monthly averages and financial yield estimation ("Bankable" for ROI). Tends to be smoother and slightly optimistic in tropical weather.
* **Solcast:** Higher temporal resolution that captures rapid cloud movements ("spikes") more accurately. Recommended for operational design (inverter/battery sizing).
* **Ground Sensors:** Essential for calibration. Raw data contains significant noise which was successfully mitigated using Kalman Filtering.

## 📂 Project Structure
```text
├── data/                   # Raw and processed CSV files
├── notebooks/              # Jupyter/Colab notebooks for analysis
│   ├── 01_CAMS_API_Fetch.ipynb
│   ├── 02_Sensor_Kalman_Filter.ipynb
│   └── 03_Interactive_Comparisons.ipynb
├── scripts/                # Standalone Python scripts
└── README.md               # Project documentation
