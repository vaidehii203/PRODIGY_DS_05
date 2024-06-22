# PRODIGY_DS_05
Analyzing traffic accident data to identify patterns related to road conditions, weather, and time of day. Visualization of accident hotspots and contributing factors.

# Traffic Accident Analysis and Visualization

This project analyzes traffic accident data to identify patterns related to various factors such as time of day, day of the week, month, state-wise distribution, weather conditions, road conditions, contributing factors, and state-wise total deaths ratio by timing of day.

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Setup](#setup)
- [Data Preprocessing](#data-preprocessing)
- [Analysis and Visualization](#analysis-and-visualization)
  - [Accidents by Timing of Day](#accidents-by-timing-of-day)
  - [Accidents by Day of the Week](#accidents-by-day-of-the-week)
  - [Accidents by Month](#accidents-by-month)
  - [Accidents by State](#accidents-by-state)
  - [Accidents by Weather Condition and Timing of Day](#accidents-by-weather-condition-and-timing-of-day)
  - [Accidents by Road Condition and Timing of Day](#accidents-by-road-condition-and-timing-of-day)
  - [Accidents by Contributing Factors](#accidents-by-contributing-factors)
  - [State-wise Total Deaths Ratio by Timing of Day](#state-wise-total-deaths-ratio-by-timing-of-day)
- [Insights and Conclusions](#insights-and-conclusions)

## Introduction
This project aims to analyze traffic accident data and provide insights based on various factors. The analysis includes visualizations to help understand patterns and contributing factors to traffic accidents.

## Dataset
The dataset used in this project contains the following columns:
- `AccidentDate`: Date of the accident (format: YYYY-MM-DD)
- `Timing`: Time of the day (e.g., Morning, Night)
- `State`: State where the accident occurred
- `WeatherCondition`: Weather condition during the accident
- `RoadCondition`: Road condition during the accident
- `Deaths`: Number of deaths in the accident
- `Reason`: Reason for the accident

## Setup
Clone the repository:

Copy code
git clone https://github.com/your-username/traffic-accident-analysis.git
cd traffic-accident-analysis

# Install the required packages:

pip install pandas numpy matplotlib seaborn

Place your dataset file (accident_data.csv) in the repository directory.

Data Preprocessing
Load and preprocess the data:

python
Copy code
import pandas as pd

# Load the data from the CSV file
df = pd.read_csv('accident_data.csv')

# Handle missing values and preprocess date and time columns
df = df.dropna()
df['AccidentDate'] = pd.to_datetime(df['AccidentDate'], format='%Y-%m-%d')
df['DayOfWeek'] = df['AccidentDate'].dt.day_name()
df['Month'] = df['AccidentDate'].dt.month_name()
Analysis and Visualization
Accidents by Timing of Day
Analyze and visualize the distribution of accidents by timing of day:

python
Copy code
import matplotlib.pyplot as plt
import seaborn as sns

plt.figure(figsize=(10, 6))
sns.countplot(x='Timing', data=df, palette='viridis')
plt.title('Distribution of Accidents by Timing of Day')
plt.xlabel('Timing of Day')
plt.ylabel('Number of Accidents')
plt.show()
Accidents by Day of the Week
Analyze and visualize the distribution of accidents by day of the week:

python
Copy code
plt.figure(figsize=(10, 6))
sns.countplot(x='DayOfWeek', data=df, palette='viridis', order=['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'])
plt.title('Distribution of Accidents by Day of the Week')
plt.xlabel('Day of the Week')
plt.ylabel('Number of Accidents')
plt.show()
Accidents by Month
Analyze and visualize the distribution of accidents by month:

python
Copy code
plt.figure(figsize=(10, 6))
sns.countplot(x='Month', data=df, palette='viridis', order=['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'])
plt.title('Distribution of Accidents by Month')
plt.xlabel('Month')
plt.ylabel('Number of Accidents')
plt.show()
Accidents by State
Analyze and visualize the distribution of accidents by state:

python
Copy code
plt.figure(figsize=(10, 6))
sns.countplot(x='State', data=df, palette='viridis')
plt.title('Distribution of Accidents by State')
plt.xlabel('State')
plt.ylabel('Number of Accidents')
plt.xticks(rotation=90)
plt.show()
Accidents by Weather Condition and Timing of Day
Analyze and visualize the distribution of accidents by weather condition and timing of day:

python
Copy code
plt.figure(figsize=(10, 6))
sns.countplot(x='WeatherCondition', hue='Timing', data=df, palette='viridis')
plt.title('Distribution of Accidents by Weather Condition and Timing of Day')
plt.xlabel('Weather Condition')
plt.ylabel('Number of Accidents')
plt.xticks(rotation=45)
plt.show()
Accidents by Road Condition and Timing of Day
Analyze and visualize the distribution of accidents by road condition and timing of day:

python
Copy code
plt.figure(figsize=(10, 6))
sns.countplot(x='RoadCondition', hue='Timing', data=df, palette='viridis')
plt.title('Distribution of Accidents by Road Condition and Timing of Day')
plt.xlabel('Road Condition')
plt.ylabel('Number of Accidents')
plt.xticks(rotation=45)
plt.show()
Accidents by Contributing Factors
Analyze and visualize the distribution of accidents by contributing factors:

python
Copy code
plt.figure(figsize=(10, 6))
sns.countplot(x='Reason', data=df, palette='viridis')
plt.title('Distribution of Accidents by Contributing Factors')
plt.xlabel('Contributing Factors')
plt.ylabel('Number of Accidents')
plt.xticks(rotation=45)
plt.show()
State-wise Total Deaths Ratio by Timing of Day
Analyze and visualize the state-wise total deaths ratio by timing of day:

python
Copy code
# State-wise total deaths ratio by timing of day
state_timing_deaths = df.groupby(['State', 'Timing'])['Deaths'].sum().unstack().fillna(0)
state_timing_deaths_ratio = state_timing_deaths.div(state_timing_deaths.sum(axis=1), axis=0)

# Plot the state-wise total deaths ratio by timing of day
state_timing_deaths_ratio.plot(kind='bar', stacked=True, figsize=(14, 7), colormap='viridis')
plt.title('State-wise Total Deaths Ratio by Timing of Day')
plt.xlabel('State')
plt.ylabel('Ratio of Deaths')
plt.xticks(rotation=90)
plt.legend(title='Timing of Day', bbox_to_anchor=(1.05, 1), loc='upper left')
plt.show()
