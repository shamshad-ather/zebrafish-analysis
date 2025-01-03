# Fish Tracking Analysis: Interpretation Guide

This document provides guidance on understanding the output generated by the fish tracking analysis tool. It explains the relevance of each plot and data point, as well as how to interpret them in general.

## I. CSV Output Files:

### 1. `individual_fish_summary.csv`

This file contains summary statistics for each fish across the specified time range.

*   **`fish_number`**: A unique identifier for each fish being tracked (1, 2, 3, etc.).

*   **`upper_time`**: The total time (in seconds) that the fish spent in the upper half of the tank during the analyzed time frame. This can indicate preference for vertical location in the tank.

    *   **Interpretation:** Higher values might suggest a preference for the upper region of the tank, possibly due to surface interaction or light.

*   **`lower_time`**: The total time (in seconds) that the fish spent in the lower half of the tank during the analyzed time frame. This can also indicate preference for vertical location.

    *   **Interpretation:** Higher values may show a preference for the lower part of the tank, perhaps related to bottom-dwelling behaviour or avoiding light.

*   **`average_speed`**: The average speed (in cm/s) of the fish across the analysed time range. This is an indication of the fish overall activity.

    *   **Interpretation:** Higher values mean a faster moving fish on average, while lower values mean a slower moving fish.

*   **`average_acceleration`**: The average acceleration (in cm/s^2) of the fish across the analysed time range. Positive values show an average increase in speed while negative ones show average deceleration.

    *   **Interpretation:** higher values show a fish that is changing speed more often, while smaller values show a fish that is consistently moving at a similar speed.

*   **`total_distance`**: The total distance (in cm) that the fish traveled in the tank across the analysed time range.

    *   **Interpretation:** a higher total distance indicates a more active fish in terms of movement.


### 2. `fish_movement_over_time.csv`

This file contains detailed fish movement data for each frame.

*   **`x1`, `y1`, `x2`, `y2`, ...**: X and Y coordinates (in cm) for each fish, with fish being numbered 1, 2, 3, etc. These values show the fish position in the tank at each frame.
    *   **Interpretation:** These show the position of each fish at a given time.

*   **`frame_number`**: The frame number, this provides an index in the video.

*   **`distance1`, `distance2`, ...**: The distance (in cm) the fish moved in the current frame relative to the previous frame.
    *   **Interpretation:** A higher value indicates more movement at that frame, while a smaller value indicates small movement.

*    **`speed1`, `speed2`, ...**: The speed (in cm/s) at which each fish is moving in the current frame.

       *    **Interpretation**: This corresponds to how quickly the fish is moving in this frame.

*   **`acceleration1`, `acceleration2`, ...**: The acceleration (in cm/s^2) of each fish in the current frame relative to the previous frame.

    *   **Interpretation:** Indicates the rate of change of the fish speed at each frame.

*   **`angle1`, `angle2`, ...**: The movement angle (in degrees) of the fish in the current frame, relative to the previous frame. 0 means movement to the right, 90 means forward, 180 means left and 270 mean backward.

    *  **Interpretation:** Shows the angle of movement for each fish relative to the previous position.

*   **`polarity1`, `polarity2`, ...**: Indicates the direction of movement of the fish (forward, backward, or other) based on its angle relative to its heading.
    * **Interpretation:** Shows if the fish is mainly moving forward, backward or in another direction relative to its orientation.

*    **`cumulative_distance1`, `cumulative_distance2`,...**: The cumulative distance (in cm) each fish has travelled from the beginning of the data to that specific frame.

       * **Interpretation:** The total distance traveled by the fish at a specific frame.

*   **`group_centroid_x`**: The average X coordinate of all fish at the current frame.

*    **`group_centroid_y`**: The average Y coordinate of all fish at the current frame.

       *    **Interpretation:** These represent the center of the group of fish at each frame.

*    **`pairwise_distances`**: A list of all pairwise distances between the fish at the current frame.

       *  **Interpretation:** The distance between all fish at a given time.

*   **`mean_pairwise_distance`**: The average of all pairwise distances between the fish at the current frame.

    *   **Interpretation**: Shows the average dispersion of the fish group at each frame.

*   **`std_pairwise_distance`**: The standard deviation of all pairwise distances between the fish at the current frame.

    *   **Interpretation**: Shows the variation in the distances between fish in the group at each frame.

## II. Plot Output Files:

### 1. `density_heatmap.png`

*   **Description:** This heatmap visualizes the distribution of all fish positions over the entire recording.
*   **Interpretation:**
    *   **Color Intensity:** Brighter areas (yellow/red) show regions of the tank where fish spent more time, indicating preferred areas or zones of activity.
    *   **Spatial Distribution:** Shows overall distribution of the fish in the tank.

### 2. `tank_structure_plot.png`

*   **Description:** This plot shows the dimensions of the tank, defines the four quadrants, marks the central area, and shows the trajectories of the fish.
*   **Interpretation:**
    *   **Tank Boundary:**  The black dashed line represents the physical boundaries of the tank.
    *   **Corner Quadrants**: The four shaded regions in the corners highlights important regions of the tank.
    *   **Center Rectangle**: The light blue rectangle in the center of the tank represent the center zone.
    *   **Trajectories**: Shows the movement paths of each fish throughout the experiment, which helps to visualise the overall activity of each fish.

### 3. `mean_pairwise_distance.png`
*   **Description:** This plot displays the average pairwise distance between all fish over time. Each point represents the `mean_pairwise_distance` at a specific frame from your `fish_movement_over_time.csv` file

*   **Interpretation:**
    *   **Vertical Axis (y):** Represents the average distance between all fish in the group (in cm).
    *   **Horizontal Axis (x):** Represents time (frame number).
    *   **Trends:**
        *   **Increasing Trends**: This indicates that the fish group is becoming more dispersed over time.
        *   **Decreasing Trends**: This shows that the fish are becoming closer to each other, indicating possible schooling or aggregation.
        *   **Stable Trends**: Shows a stable dispersion among the fish group, where fish keep their distance.
        *   **Oscillations**: Shows the group is periodically becoming more dispersed and more aggregated.
          
### 4. `group_centroid_trajectory.png`

*   **Description:** This plot shows the path taken by the center of the fish group (group centroid) over the entire experiment. It shows the x and y positions of the group's centroid over time.

*   **Interpretation:**
    *   **Trajectory Path:**  The line on the plot shows the path the center of the group takes over time.
    *   **Location Preference:** The plot may reveal if the group as a whole tends to stay in specific regions of the tank.
    *   **Directional Movement:** Helps in understanding if the group is moving in a specific direction or exploring the tank randomly.
    *    **Cluster:** Areas of a tighter trajectory (clusters) show where the group spent more time.
 
### 5. `individual_fish_plots/` (Folder)

This folder contains a number of plots for each fish.

*   **`fish{fish_num}_kde_plot.png`**:
    *   **Description**: KDE plot for the spatial distribution of the fish.
    *   **Interpretation**: Shows the distribution of the fish within the tank with higher probability regions highlighted.

*  **`fish{fish_num}_radial_distribution.png`**:
    * **Description**: Histogram showing the distribution of fish distances from the center of the tank.
    * **Interpretation**: It helps to see if the fish prefer the centre or the periphery.

*   **`fish{fish_num}_angle_of_movement.png`**:
    *   **Description**: Histogram of the angle at which the fish is moving over time.
    *   **Interpretation**: Shows the direction preference of the fish.

*  **`fish{fish_num}_speed_timeseries.png`**:
    *   **Description**: Time series plot of the fish speed.
    *   **Interpretation**: Shows how the speed of the fish varies over time.

*  **`fish{fish_num}_acceleration_timeseries.png`**:
    *   **Description**: Time series plot of the fish acceleration.
    *   **Interpretation**: Shows how the acceleration of the fish varies over time.

*  **`fish{fish_num}_polar_plot.png`**:
    *   **Description**: Polar plot of the movement directions.
    *   **Interpretation**: Shows if the fish prefers a certain direction.

*   **`fish{fish_num}_occupancy_plot.png`**:
    *   **Description**: Occupancy plot showing the time spent by fish in different areas of the tank.
    *   **Interpretation**: Shows where the fish spends most of its time.

*   **`fish{fish_num}_smoothness_plot.png`**:
    *   **Description**: Trajectory Smoothness plot, showing the changes in angle of movement.
    *  **Interpretation**: Shows how often the fish is changing its movement angle.

## III. General Interpretation Guidelines:

*   **Vertical Distribution**: Time spent in upper and lower halves (`upper_time`, `lower_time`) can reflect behaviours like surface feeding or bottom dwelling.

*   **Activity Levels**: Average speed and total distance can reveal differences in activity between fish. Higher speeds and distances means a more active fish.

*   **Group Dynamics:** Mean pairwise distance and standard deviation indicate if the group is tightly packed or more dispersed.

*   **Individual Trajectories**: Comparing individual fish plots and data highlights any differences between fish's behaviour.

*   **Experimental Context**: Always interpret results in light of the experimental setup and conditions. Consider factors like lighting, food availability, and tank size.

By using this guide, you should gain a better understanding of the fish tracking data and how to interpret its different aspects. Remember that context is crucial; combine what you learn from the data with your knowledge of the experiment for the best analysis.
