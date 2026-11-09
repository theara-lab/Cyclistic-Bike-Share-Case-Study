# Cyclistic Bike-Share Case Study: Casual Riders vs. Annual Members

## 1. Business Task
Cyclistic wants to convert casual riders into annual members. To help achieve this goal, I analyzed and compared the riding behavior of casual riders and members to identify key differences in their riding patterns. These findings will be used to develop targeted marketing recommendations aimed at encouraging casual riders to become members.

## 2. Data Source
* **Source:** 2025 Divvy trip data, made available by Motivate International Inc.
* **Scope:** January to December 2025 across 12 monthly CSV files, totaling 5,552,994 raw records.
* **Parameters:** Timestamps, starting/ending stations, geographic coordinates, rideable type, and rider type.
* **Limitation:** The dataset does not contain unique customer identifiers, meaning the analysis focuses on individual trips rather than unique users.

## 3. Data Cleaning and Manipulation
Before conducting the analysis, I cleaned and prepared the dataset to ensure data integrity:
* **Date-Range Check:** Found and excluded 53 anomalous records from December 31, 2024, to isolate 2025 data exclusively.
* **Duplicate Check:** Ran a duplicate ride ID check; zero duplicate IDs were found.
* **Missing Values:** Missing values were identified in start/end station fields and coordinates. These records were retained as those fields were not required for this specific analysis.
* **Ride-Duration Filtering:** Excluded invalid rows including 29 negative durations, 1,808 zero-second durations, and 5,585 rides lasting over 24 hours. Valid rides under 1 minute were preserved.
* **Feature Engineering:** Calculated overall ride duration in minutes and extracted fields for `day_of_week`, `day_of_week_number`, and `time_of_day`.
* **Final Dataset:** The final analysis population resulted in **5,545,519 clean records**.

### Technical Implementation Details
* **Google Colab (Python):** Utilized Python to handle the heavy computational load of merging and downsizing the individual 100MB+ monthly CSV files, preventing local system crashes.
* **Google BigQuery (SQL):** Uploaded the optimized datasets into BigQuery to execute aggregation queries, calculating average durations, seasonal trends, and timeframe breakdowns.
* **Looker Studio:** Connected directly to the database layer to build the visualization reporting dashboard.

## 4. Summary of Analysis
* **Ride Duration:** Casual riders maintain a significantly longer average ride duration (19.13 minutes) compared to annual members (11.95 minutes). 
* **Threshold Endurance:** The gap between user types expands drastically on longer rides. Casual trips exceed the 30-minute threshold at nearly triple the rate of members (14.95% vs. 5.31%).
* **Weekly Patterns:** Members dominate weekday volume (accounting for ~69%-72% of trips). However, casual ridership surges on weekends, claiming 47.86% of all Saturday traffic and 46.40% of Sunday traffic.
* **Seasonality:** Casual riding is heavily weather-dependent. Casual ride share peaks sharply in the summer months of June (42.95%), July (42.30%), and August (42.71%), compared to a low of 17.37% in January.
* **Time of Day:** Casual riders make up their highest percentage share of the market at night (48.38%) compared to morning commute hours (28.43%).

## 5. Visualizations & Findings

### 5.1 Average Ride Duration by Rider Type<img width="500" height="332" alt="Capstone Project_Duration   day of week_Bar chart (1)" src="https://github.com/user-attachments/assets/2a20990e-addb-44b8-8df7-6fc8227d9c79" />

<img width="500" height="332" alt="Capstone Project_Duration   day of week_Bar chart" src="https://github.com/user-attachments/assets/206a63d5-4c5f-4382-86ad-5e99e5b61523" />

* **Finding:** Casual rides averaged 19.13 minutes, compared with 11.95 minutes for member rides.

### 5.2 Ride Duration Thresholds by Rider Type<img width="500" height="332" alt="Capstone Project_Duration   day of week_Bar chart (2)" src="https://github.com/user-attachments/assets/04b8ee39-3897-48e1-9c79-78da18ba40ef" />
<img width="500" height="332" alt="Capstone Project_Duration   day of week_Bar chart (2)" src="https://github.com/user-attachments/assets/6a93a7d9-724a-4b1e-b4dc-4da9110c868e" />

<img width="500" height="332" alt="Capstone Project_Duration   day of week_Bar chart (1)" src="https://github.com/user-attachments/assets/d90d34e5-70ba-4d80-80af-9eae80a5a22f" />

* **Finding:** Casual riders consistently exhibit a higher percentage of long-duration trips than members across 15, 20, and 30-minute markers.

### 5.3 Rides by Day of Week
<img width="500" height="332" alt="Capstone Project_Duration   day of week_Bar chart (2)" src="https://github.com/user-attachments/assets/270a746b-be3e-4fb9-ac18-a8f97d3eeb9e" />

* **Finding:** Members maintain high, stable volume on weekdays for routine utility, while casual riders peak on Saturday and Sunday for leisure.

### 5.4 Monthly Rides by Rider Type
<img width="500" height="332" alt="Capstone Project_Month   time of day_Time series" src="https://github.com/user-attachments/assets/73a0e1cf-b643-4542-b86a-b6aaafb3a9a0" />
* **Finding:** Casual ridership is highly seasonal, concentrating heavily during June, July, and August.

### 5.5 Rides by Time of Day
<img width="500" height="332" alt="Capstone Project_Month   time of day_Bar chart" src="https://github.com/user-attachments/assets/72a05d2f-18ee-406e-b219-70448b88e74d" />

* **Finding:** While the afternoon holds the highest total absolute volume of casual rides, night rides represent the highest percentage share of casual activity.

## 6. Recommendations
1. **Target Long-Duration Riders:** Introduce targeted membership promotional campaigns inside the app explicitly targeting casual riders who exceed 15-minute durations. Highlight the clear cost savings of an annual membership versus repeated casual single-trip fees.
2. **Weekend-Specific Digital Strategy:** Focus digital marketing real estate and app notification campaigns on weekend casual users. Offer weekend-centric trials or special promotional conversion rates immediately following a Saturday or Sunday ride completion.
3. **Summer Seasonal Campaigns:** Launch aggressive acquisition campaigns immediately leading up to June, maintaining high visibility through July and August. Introduce summer-pass tiers that provide an easy stepping stone toward full annual memberships.
