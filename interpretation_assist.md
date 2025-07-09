# Fish Tracking Analysis: A Comprehensive Interpretation Guide

## Introduction

This guide provides a detailed walkthrough for interpreting the data and visualizations produced by the fish tracking analysis script. The goal is to move beyond simply defining metrics and to understand them as quantitative representations of complex animal behavior. This document will help you translate the numerical output into a rich narrative about the fish's experience, whether it relates to anxiety, social interaction, activity levels, or fear responses.


## I. Summary Data Files (.csv)

These files represent the final, high-level summary of behavior, distilled into a format ready for statistical analysis. Each file focuses on a different behavioral domain, with one row per fish.

### 1. `distance_speed.csv`: Locomotor Activity

*   **Purpose:** Provides a fundamental snapshot of how active each fish was. This is the primary output for assessing general exploratory behavior and the effects of stimulants or sedatives.
*   **Metrics:**
    *   **`total_distance` (cm):** The complete distance the fish traveled during the analyzed time.
        *   **Interpretation:** This is the most direct measure of overall activity. A high value signifies a highly active, exploratory fish. A low value suggests lethargy or hypoactivity. This metric is sensitive to drugs that affect motor function.
    *   **`average_speed` (cm/s):** The total distance traveled divided by the total duration of the analysis.
        *   **Interpretation:** This metric quantifies the *pace* of the fish's movement. It distinguishes between a fish that covers distance through slow, constant movement and one that does so via short, high-speed bursts. Comparing it with `total_distance` can reveal different movement strategies.

### 2. `time_in_halves.csv`: Vertical Space Preference

*   **Purpose:** Quantifies the fish's preference for the upper vs. lower sections of the water column.
*   **Metrics:**
    *   **`Upper` / `Lower` (seconds):** The total time spent in the top and bottom halves of the tank.
        *   **Interpretation:** In zebrafish and many other aquatic species, vertical position is a key indicator of state. A strong preference for the lower half (`Lower` time is high) is a classic anxiogenic (anxiety-like) response, often interpreted as a predator-avoidance strategy. Conversely, more time in the upper half may indicate reduced anxiety or specific behaviors like surface exploration.

### 3. `time_in_zones.csv`: Thigmotaxis & Anxiety

*   **Purpose:** Measures the classic anxiety-related behavior of thigmotaxis, or "wall-hugging." This is one of the most robust metrics from the **Novel Tank Test**.
*   **Metrics:**
    *   **`Center` / `Periphery` (seconds):** The total time the fish spent in the exposed, open central area versus the "safer" zone along the tank walls.
        *   **Interpretation:** This represents a trade-off between exploration (risk) and safety. A confident, calm fish is more likely to explore the entire environment, resulting in a higher `Center` time. A stressed or anxious fish will avoid the open, exposed center and spend the vast majority of its time in the `Periphery`. A high periphery-to-center time ratio is a very strong indicator of an anxiogenic state.

### 4. `freezing_analysis.csv`: Fear Response

*   **Purpose:** Quantifies the "freezing response," an active defensive state characterized by complete immobility.
*   **Metrics:**
    *   **`total_freeze_time_s` (seconds):** The cumulative duration of all freezing episodes. It tells you *how long* the fish was in a frozen state.
    *   **`num_bouts`:** The number of distinct times the fish initiated a freezing response. It tells you *how often* the fish was startled into freezing.
        *   **Interpretation:** Freezing is a primary and evolutionarily conserved fear response, distinct from simple inactivity. It is often triggered by a sudden, threatening stimulus (e.g., a shadow, a tap on the tank). An increase in *both* the duration and number of freezing bouts is powerful evidence of a heightened fear state.

### 5. `turning_analysis.csv`: Motor Control & Lateralization

*   **Purpose:** Analyzes directional preference and motor patterns.
*   **Metrics:**
    *   **`left_turns` / `right_turns`:** A count of sharp turns exceeding a defined angle.
    *   **`turn_bias_index`:** A normalized index from -1 (exclusively right turns) to +1 (exclusively left turns). A value near 0 indicates balanced turning.
        *   **Interpretation:** While some natural variation exists, a strong and persistent turning bias can indicate neurological issues, stress-induced stereotypic behavior (repetitive circling), or the effects of compounds that affect brain lateralization.


## II. Detailed & Intermediate Files

### `fish_analysis_results.csv`
This is the "master" data file, containing frame-by-frame data for every calculated metric. While the summary files are better for statistics, this file is invaluable for:
*   Visualizing fine-grained temporal dynamics (e.g., plotting speed just before and after a stimulus).
*   Creating custom analyses and plots not included in the script.
*   Debugging or deeply understanding how the summary metrics are derived from the raw data.

### `trajectories_cleaned.csv`
This file is a quality-control checkpoint. It contains the x,y coordinates after the script has performed its initial cleaning and interpolation. Its main use is to confirm that the pre-processing step worked correctly before the main analysis began.


## III. Plot Output Files (`plots/` folder)

Visualizations provide an intuitive understanding of the data that numbers alone cannot.

### Group-Level Plots

*   **`overlaid_trajectory.png`**:
    *   **What It Shows:** The complete movement path of every fish, color-coded, on a single map of the tank.
    *   **How to Interpret:** This is your first, high-level overview. You can immediately see if one fish was significantly less active (a very small, dense scribble) or if all fish avoided a certain area. It provides a gut-check on the overall experiment.

*   **`pairwise_distance.png`**:
    *   **What It Shows:** A time-series plot of the average distance between all pairs of fish. The shaded region represents the standard deviation, indicating the uniformity of the group's spacing.
    *   **How to Interpret:** This is the key plot for **Shoaling** or **Schooling** behavior.
        *   **A low and stable line with a narrow shaded band:** The signature of a tight, cohesive shoal. The fish are actively maintaining a consistent, close distance to one another.
        *   **A high and stable line:** The fish are dispersed but not necessarily avoiding each other. They are moving independently.
        *   **A wildly fluctuating line:** Suggests dynamic group behavior, such as the group expanding to explore and then contracting in response to a perceived threat.
        *   **A wide shaded band:** Indicates an irregular group formation, where some fish are clustered together while others are far away.

*   **`group_kde_plot.png`**:
    *   **What It Shows:** A 2D "heatmap" of where the fish, as a collective group, spent the most time.
    *   **How to Interpret:** Hotter colors (yellow/red) indicate regions of high occupancy. This can reveal if the *entire shoal* exhibited a preference for a specific corner or showed collective thigmotaxis (a bright ring around the edge of the plot).

### Individual Fish Plots

*(Note: `i` in the filenames corresponds to the fish number, e.g., `Fish 1_kde_plot.png`)*

*   **`Fish i_kde_plot.png`**:
    *   **What It Shows:** A personalized heatmap for a single fish.
    *   **How to Interpret:** This is the most powerful visual tool for assessing an individual's spatial preference. Thigmotaxis is vividly shown as a "halo" of high activity around the periphery, with a "cold" blue center. You can easily spot preferences for corners or specific tank features.

*   **`Fish i_radial_distribution.png`**:
    *   **What It Shows:** A histogram quantifying how much time the fish spent at different distances from the tank's center.
    *   **How to Interpret:** This is the numerical backup for the KDE plot. A large bar on the far right of the histogram corresponds to time spent at the edge (periphery), providing quantitative evidence for thigmotaxis. A more centered distribution indicates a fish that comfortably explored the entire tank.

*   **`Fish i_speed_timeseries.png`**:
    *   **What It Shows:** A line graph of the fish's instantaneous speed over the entire trial, like a "behavioral EKG."
    *   **How to Interpret:** This plot reveals the rhythm of the fish's activity.
        *   **Sharp Peaks:** Indicate "bursts" of high-speed movement, possibly escape responses or exploratory darts.
        *   **Long, Flat Valleys at or near zero:** This is the visual signature of the freezing bouts. You can see precisely *when and for how long* the fish was immobile, providing temporal context to the `freezing_analysis.csv` summary.
        *   **Baseline Level:** The overall average height of the line indicates the fish's general activity level.