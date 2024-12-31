# Zebrafish Tracking Analysis

This repository contains a Python-based analysis tool for analyzing cordinate files obtained after tracking the video, designed to provide both individual fish metrics and group dynamics. The analysis is performed using a Jupyter Notebook (`.ipynb` file), which allows for easy viewing, modification, and execution of the code.

## Table of Contents

1.  **Overview**
2.  **Requirements**
3.  **Setup**
4.  **Input Data Format**
5.  **Configuration**
6.  **Analysis Steps**
7.  **Output**
8. **Additional Information**

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
