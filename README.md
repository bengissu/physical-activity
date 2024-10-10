# Physical Activity Analysis for Wearable Products

This repository contains the project **Physical Activity Analysis for a Wearable Product**.

## Project Overview

The goal of this project is to produce a product that can predict the type of physical activity being performed and the duration of the activity in seconds. Using data collected from various sensors on wearable devices, the project aims to provide actionable insights that help optimize data collection for better cost-efficiency and accuracy.

## Dataset

The **Physical Activity Monitoring** dataset contains data from 9 subjects performing 18 different activities. These activities range from everyday movements like walking, sitting, and ironing to more vigorous actions like running, playing soccer, and rope jumping. The subjects were equipped with three Inertial Measurement Units (IMUs) and a heart rate monitor.

### Key Dataset Information:
- **Subjects**: 9
- **Activities**: 18 (e.g., walking, running, cycling, house cleaning, playing soccer)
- **Sensor Data**: Timestamp, heart rate, accelerometer, magnetometer, gyroscope, orientation data
- **IMU Locations**: Hand, chest, ankle
- **Subject Features**: Sex, age, weight, height, resting HR, max HR, dominant hand

The data is stored in three matrices:
1. **Subject Features Matrix**: Contains demographic and physical information about the subjects.
2. **Activity Times Matrix**: Times of activities performed by the subjects.
3. **Activity Data Matrix**: Sensor readings while the subjects performed the activities.


## Data Processing

### Data Cleaning
- Orientation data was marked as 'invalid' and excluded from analysis as recommended by data collectors.
- Transient activities were removed as they were deemed unsuitable for analysis.
- Activity times were merged with the main dataset, and rows containing `NaN` values were removed.

### Data Splitting
- The dataset was split into **training** and **testing** sets.
- The training data was used for in-depth analysis, correlation study, and model building.

## Analysis and Modeling

### Exploratory Data Analysis (EDA)
- Correlation analysis between timestamp, heart rate, accelerometer, magnetometer, and gyroscope data was visualized using heatmaps.
- Relationships between different sensors and activity types were investigated.

### Hypothesis Testing
Due to a limited number of subjects, the analysis focused on differences in sensor readings across activities:
- **Lying down**: Higher chest accelerometer and magnetometer readings and a lower heart rate.
- **Cycling**: Lower chest accelerometer readings compared to other activities.
- **Running**: Higher heart rate compared to other activities.

### Predictive Modeling
1. **Activity Duration Prediction**: 
   - A **linear regression model** was developed to estimate the time taken by a subject for each activity.
   - Results indicated that some sensor data could be excluded without significant loss in accuracy, offering potential cost savings.

2. **Activity Identification**:
   - A **decision tree classifier** was built to predict the activity ID.
   - The model achieved about **98% accuracy** using the complete dataset.
   - Using only chest and ankle temperatures along with heart rate slightly increased model performance.

### Actionable Insights
- **Sensor Optimization**: To reduce costs, certain measurements can be excluded:
  - **Gyroscope data** showed weak correlations with other sensor data, making it a candidate for removal if cost reduction is a priority.
  - **Using only ankle temperature, chest temperature, and heart rate** provided similar results in predicting activity duration and ID, suggesting these measurements could be sufficient for product development.
  
- **Model Performance**:
  - The **decision tree classifier** is highly effective for activity recognition with minimal sensor input.
  - The linear regression model for activity duration remains accurate with reduced sensor data, though it introduces a slight increase in error.

## Conclusions

The analysis suggests that a wearable product focusing on collecting **ankle temperature, chest temperature, and heart rate** would be more cost-effective while maintaining high accuracy in predicting both activity type and duration. This could significantly streamline product development for wearable technology targeting physical activity monitoring.

## Project Structure

- `README.md`: This file, providing an overview of the project.
- `analysis.ipynb`: Jupyter notebook containing data analysis, hypothesis testing, and model development.

## Getting Started

### Prerequisites

To run this project, you'll need:

- Python 3.7+
- Jupyter Notebook
- The following Python libraries:
  - pandas
  - numpy
  - matplotlib
  - seaborn
  - scikit-learn

You can install the necessary libraries using:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### Running the Notebook

1. Clone the repository:
   ```bash
   git clone https://github.com/bengissu/physical-activity.git
   ```
2. Navigate to the project folder:
   ```bash
   cd physical-activity
   ```
3. Open the Jupyter notebook:
   ```bash
   jupyter notebook analysis.ipynb
   ```

## References
- A. Reiss and D. Stricker. Introducing a New Benchmarked Dataset for Activity Monitoring. *The 16th IEEE International Symposium on Wearable Computers (ISWC)*, 2012.
- A. Reiss and D. Stricker. Creating and Benchmarking a New Dataset for Physical Activity Monitoring. *The 5th Workshop on Affect and Behaviour Related Assistance (ABRA)*, 2012.

## Contributing

Contributions are welcome! Feel free to fork this repository and create a pull request with your improvements or new features.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Feel free to make any further adjustments based on your needs!
