# Dashboard_Airpollution
This interactive dashboard provides insights into the road casualties in the city Town of Carry, in North Carolina.

## Introduction

Traffic accidents are a critical issue for public safety and urban planning. In the state of North Carolina, as in many other regions, understanding the factors that contribute to traffic accidents is essential for making informed decisions about road safety, infrastructure development, and law enforcement. This project aims to analyze and visualize traffic accident data to uncover patterns, trends, and key factors that influence accident rates.

The dataset includes detailed records of traffic accidents across the state, spanning multiple years (2020-2024). By analyzing various attributes such as accident location, vehicle types involved, road conditions, weather, and more, the goal is to provide a comprehensive understanding of traffic accident trends in North Carolina.

Through the development of an interactive dashboard, users can explore the data, filter by year and month, and gain insights into accident frequency, vehicle involvement, road conditions, and lighting conditions. This analysis is not only useful for researchers but also for policymakers, urban planners, and law enforcement agencies seeking to reduce accidents and improve road safety across the state.

## Traffic Accident Dashboard Report - North Carolina

<h1>1. Project Overview</h1>

This project aims to develop an interactive dashboard to analyze and visualize traffic accident data in North Carolina. The dashboard provides insights into accident trends, vehicle types, road conditions, and more, helping stakeholders make informed decisions about traffic safety and policy improvements.

<h1>Input Dataset</h1>

The data used in this project consists of traffic accident records in North Carolina. The dataset includes various attributes such as accident location, road features, conditions, and vehicle types. The data spans multiple years (2020-2024), and is used to create various visualizations and analyses, allowing users to filter by year and month.

The initial data is download from <a href='https://catalog.data.gov/dataset/crash-data'>here</a>.

| Column Name                  | Description                                                                                 |
|------------------------------|---------------------------------------------------------------------------------------------|
| `tamainid`                    | Unique identifier for each accident.                                                        |
| `location_description`        | A description of the accident's location (e.g., street, intersection, etc.).                |
| `rdfeature`                   | Road feature (e.g., intersection, driveway, etc.).                                          |
| `rdcharacter`                 | Road characteristics (e.g., straight, level, etc.).                                         |
| `rdclass`                     | Type of road classification.                                                                 |
| `rdconfigur`                  | Road configuration (e.g., two-way, divided, etc.).                                          |
| `rdsurface`                   | Road surface condition (e.g., smooth asphalt, coarse asphalt, etc.).                        |
| `rdcondition`                 | Road condition (e.g., dry, wet, icy, etc.).                                                  |
| `Conditions`                  | Weather or road conditions during the accident.                                             |
| `lightcond`                   | Lighting conditions during the accident (e.g., dark, daylight, etc.).                        |
| `day_night`                   | Whether the accident occurred during the day or night.                                      |
| `weather`                     | Weather conditions during the accident (e.g., clear, cloudy, rain, etc.).                    |
| `trafcontrl`                  | Traffic control type (e.g., stop and go signal, no control, etc.).                          |
| `lat` and `lon`               | Latitude and longitude coordinates of the accident location.                                 |
| `fatality`                    | Whether the accident involved fatalities (1 = yes, 0 = no).                                 |
| `numinjuries`                 | The number of injuries reported in the accident.                                             |
| `vehicle_type`                | Types of vehicles involved in the accident. (e.g., passenger car, sport utility, etc.).     |
| `ta_date`                     | The date the accident occurred.                                                              |
| `month`                       | The month in which the accident occurred.                                                   |
| `year`                        | The year in which the accident occurred.                                                    |

## Methodology

### Data Transformation and Cleaning

The following steps were taken to clean and transform the raw data:

1. **Vehicle Type Normalization**:  
   The `vehicle_type` column originally contained multiple vehicle types separated by a comma. I simplified this to include only the first vehicle type in each record.  
   **Formula used**:  
   ```excel
   =LEFT(H1,FIND(",",H1)-1)



