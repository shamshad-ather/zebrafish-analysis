# Fish Tracking Analysis

This repository contains a Python-based analysis tool for tracking fish movement, designed to provide both individual fish metrics and group dynamics. The analysis is performed using a Jupyter Notebook (`.ipynb` file), which allows for easy viewing, modification, and execution of the code.

## Table of Contents

1.  **Overview**
2.  **Requirements**
3.  **Setup**
4.  **Input Data Format**
5.  **Analysis Steps**
6. **Additional Information**

## 1. Overview

This tool is designed to process fish tracking data from videos. The analysis includes:

*   **Individual Fish Analysis**: Calculation of speed, acceleration, movement angles, polarity (forward/backward), and cumulative distance for each fish.
*   **Group Analysis**: Computation of group centroid, mean pairwise distance, and standard deviation of pairwise distances.
*   **Time Spent Analysis**:  Analysis of time spent by fish in the upper and lower halves of the tank, as well as average speeds and distances within a specified time range.
*   **Visualization**: Generation of various plots including density heatmaps, tank structure with quadrant divisions, and individual fish plots (KDE plots, radial distribution, angle of movement, speed and acceleration time series, polar plots, occupancy, and trajectory smoothness plots).
*  **Data Saving**: Saving of processed data in CSV files for further analysis.

## 2. Requirements

To run this analysis, you will need:

*   **Python 3.6 or later**
*   The following Python libraries:
    *   pandas
    *   numpy
    *   matplotlib
    *   seaborn
    *   scipy

You can install these libraries using pip:

```bash
pip install pandas numpy matplotlib seaborn scipy
```

## 3. Setup

1.  **Clone the Repository:**
    *   Clone the repository to your local machine:

        ```bash
        git clone https://github.com/shamshad-ather/zebrafish-analysis/
        cd zebrafish-analysis
        ```
2.  **Install Requirements:**
    *   Make sure you have the required python packages. If not install:
        ```bash
        pip install pandas numpy matplotlib seaborn scipy
        ```
3.  **Prepare Your Data:**
    *   Place your fish tracking data file (e.g., `1.csv`, `trajectory.csv`) in the same directory as the Jupyter Notebook (`.ipynb` file).

## 4. Input Data Format

The input CSV file should have the following format:

*   **Comma-Separated Values**: Each row represents a frame.
*   **Column Structure**: Columns represent x and y coordinates for each fish in the order `x1, y1, x2, y2, x3, y3...` and so on.
*   Ensure that the number of columns corresponds to the number of fish you are tracking.


## 5. Analysis Steps

1.  **Open the Jupyter Notebook:**
    *   Open the `.ipynb` file using Jupyter Notebook or Jupyter Lab.

2.  **Review Configuration:**
    *   Check the `Configuration/Constants and Input Data` section in the notebook.

3.  **Run the Analysis:**
    *   Execute all cells in the notebook by selecting "Cell" > "Run All" in the Jupyter menu.


## 6. Additional Information

*   **Customization:** You can modify the code to add more analysis or plots to suit your needs.
*   **Error Handling:**  Ensure your input CSV is correctly formatted to avoid errors.
*   **Time Range:**  To analyse a specific time window, provide the start and end frame in the configuration section.  Otherwise, the analysis will cover the entire dataset.

```
