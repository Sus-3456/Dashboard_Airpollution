# Dashboard_Airpollution
This interactive dashboard provides insights into the road casualties in the city Town of Carry, in North Carolina.
# Traffic Accident Dashboard Report - North Carolina
<h1>1. Introduction</h1>

Traffic accidents are a critical issue for public safety and urban planning. In the state of North Carolina, as in many other regions, understanding the factors that contribute to traffic accidents is essential for making informed decisions about road safety, infrastructure development, and law enforcement. This project aims to analyze and visualize traffic accident data to uncover patterns, trends, and key factors that influence accident rates.

The dataset includes detailed records of traffic accidents across the state, spanning multiple years (2020-2024). By analyzing various attributes such as accident location, vehicle types involved, road conditions, weather, and more, the goal is to provide a comprehensive understanding of traffic accident trends in North Carolina.

Through the development of an interactive dashboard, users can explore the data, filter by year and month, and gain insights into accident frequency, vehicle involvement, road conditions, and lighting conditions. This analysis is not only useful for researchers but also for policymakers, urban planners, and law enforcement agencies seeking to reduce accidents and improve road safety across the state.

<h1>2. Project Overview</h1>

This project aims to develop an interactive dashboard to analyze and visualize traffic accident data in North Carolina. The dashboard provides insights into accident trends, vehicle types, road conditions, and more, helping stakeholders make informed decisions about traffic safety and policy improvements.

<h1>3. Input Dataset</h1>

The data used in this project consists of traffic accident records in North Carolina. The dataset includes various attributes such as accident location, road features, conditions, and vehicle types. The data spans multiple years (2020-2024), and is used to create various visualizations and analyses, allowing users to filter by year and month.

The initial data is download from <a href='https://catalog.data.gov/dataset/crash-data'>here</a>. Here is a brief description of the data show in the different columns of the csv file:


| Row Number | Column Name               | Description                                                                                   |
|------------|---------------------------|-----------------------------------------------------------------------------------------------|
| 1          | `location_description`     | A description of the accident's location (e.g., street, intersection, etc.).                  |
| 2          | `rdfeature`                | Road feature (e.g., intersection, driveway, etc.).                                            |
| 3          | `rdcharacter`              | Road characteristics (e.g., straight, level, etc.).                                           |
| 4          | `rdclass`                  | Type of road classification.                                                                   |
| 5          | `rdconfigur`               | Road configuration (e.g., two-way, divided, etc.).                                            |
| 6          | `rdsurface`                | Road surface condition (e.g., smooth asphalt, coarse asphalt, etc.).                          |
| 7          | `rdcondition`              | Road condition (e.g., dry, wet, icy, etc.).                                                    |
| 8          | `lightcond`                | Lighting conditions during the accident (e.g., dark, daylight, etc.).                          |
| 9          | `weather`                  | Weather conditions during the accident (e.g., clear, cloudy, rain, etc.).                     |
| 10         | `trafcontrl`               | Traffic control type (e.g., stop and go signal, no control, etc.).                            |
| 11         | `lat`                       | Latitude coordinate of the accident location.                                                 |
| 12         | `lon`                       | Longitude coordinate of the accident location.                                                |
| 13         | `lon2`                      | Additional longitude data (if available).                                                     |
| 14         | `lat2`                      | Additional latitude data (if available).                                                      |
| 15         | `tract`                     | Census tract identifier related to the accident location.                                     |
| 16         | `zone`                      | Zone identifier related to the accident location.                                             |
| 17         | `fatality`                  | Numbers of deceased persons after the accident.                                               |
| 18         | `possblinj`                 | Possibility of injuries in the accident.                                                      |
| 19         | `numpassengers`             | Number of passengers involved in the accident.                                                |
| 20         | `numpedestrians`            | Number of pedestrians involved in the accident.                                               |
| 21         | `contrcir1_desc`            | Description of the first contributing circumstance.                                           |
| 22         | `contrcir2_desc`            | Description of the second contributing circumstance.                                          |
| 23         | `contrcir3_desc`            | Description of the third contributing circumstance.                                           |
| 24         | `contrcir4_desc`            | Description of the fourth contributing circumstance.                                          |
| 25         | `vehicle1`                  | First vehicle involved in the accident.                                                       |
| 26         | `vehicle2`                  | Second vehicle involved in the accident.                                                      |
| 27         | `vehicle3`                  | Third vehicle involved in the accident.                                                       |
| 28         | `vehicle4`                  | Fourth vehicle involved in the accident.                                                      |
| 29         | `vehicle5`                  | Fifth vehicle involved in the accident.                                                       |
| 30         | `workarea`                  | Whether the accident occurred in a work area (Yes/No).                                        |
| 31         | `records`                   | Number of records related to the accident.                                                    |
| 32         | `ta_date`                   | Date the accident occurred (in dd/mm/yyyy format).                                           |
| 33         | `ta_time`                   | Time the accident occurred (in HH:MM:SS format).                                              |
| 34         | `crash_date`                | Exact datetime the accident occurred in ISO 8601 format (YYYY-MM-DDTHH:MM:SS).               |
| 35         | `geo_location`              | Geolocation data in the format of latitude and longitude.                                     |
| 36         | `year`                      | Year the accident occurred.                                                                   |
| 37         | `fatalities`                | Whether there were fatalities in the accident.                                                 |
| 38         | `injuries`                  | Whether there were injuries in the accident.                                                   |
| 39         | `month`                     | Month when the accident occurred (numeric).                                                   |
| 40         | `contributing_factor`       | Factors contributing to the accident.                                                         |
| 41         | `vehicle_type`              | Types of vehicles involved in the accident (e.g., passenger car, sport utility, etc.).        |


The data has <strong>19.642</strong> entrances.

<h1>4. Methodology</h1>

<h2>4.1. Data Transformation and Cleaning</h2>
After understanding and analyzing the type of information provided in each column, the data was cleaned. This cleaning process involved several interventions:
<ul>
   <li>Three new time-related columns were created:
      <blockquote>Formula use to "Dia" column: =TEXTO([@[ta_date]]; "dddd")</blockquote>
      <blockquote>Formula use to "Num_dia" column: =[@DIA]</blockquote>
      <blockquote>Formula use to "Nom_Mes" column: =ELEGIR([@month]; "Enero"; "Febrero"; "Marzo"; "Abril"; "Mayo"; "Junio"; "Julio"; "Agosto"; "Septiembre"; "Octubre"; "Noviembre"; "Diciembre")</blockquote>
   </li>

   <li>A new column was created to categorize the lightcond column into two categories:
      <dd>The raw column had 5 categories, in which there were two with no usable data "OTHER" and "UNKNOWN". Those two categories are not considered for the analysis. The rest of the categories were classified into "daylight" or "darkness".</dd>
   </li>

   <li>A new column was created to convert the values in the injuries column into numeric values:
      <dd>The values with "Yes" are changed into "1" and the values with "No" are changed into "0".</dd>
      <blockquote>Formula use in column "Num_injuries": =SI([@injuries]="yes"; 1; 0)</blockquote>
   </li>

   <li>The vehicle_type column was simplified to a one or two-word description:
      <dd>the column originally contained two or three brief descriptions separated by commas, and the new column now retains only the first description.</dd>
      <blockquote>Formula use for vehicle: =LEFT([@vehicule_type]; FIND(","; [@vehicule_type] )-1)</blockquote>
   </li>

   <li>The rdcondition column was simplified:
      <dd>The new categories are: "dry", "wet", or "other".</dd>
   </li>

   <li>Blank spaces in the columns:
      <dd>vehicle_type, rdsurface, rdcondition, and weather were filled.</dd>
      <blockquote>Using filter by "Blank" and then putting "OTHER" in the columns left</blockquote>
   </li>

   <li>Data related to 2025 was removed due to being incomplete.</li>
   
   <li>A new column was created to categorize the lightcond column into two categories:
      <dd>The raw column had 5 categories, in which there were two with no usable data "OTHER" and "UNKNOWN". Those two categories are not considered for the analysis. The rest of the categories were classified into "daylight" or "darkness".</dd>
      <blockquote>Formula use for "day_night" column: =SI(ESNUMERO(ENCONTRAR("DAYLIGHT";[@lightcond])); "DAYLIGHT"; "DARK")</blockquote>
   </li>
</ul>

<h2>4.2. Removing Duplicates</h2>
Duplicates are identified using the tamainid column and the formula =CONTAR.SI(A:A;A2).
None is found.<br><br>
For the analysis these columns were used:
Here is the updated table with an additional column indicating the column number:

| **Column Number** | **Column Name**         | **Description**                                                                                           |
|-------------------|-------------------------|-----------------------------------------------------------------------------------------------------------|
| 1                 | `tamainid`              | Unique identifier for each accident.                                                                      |
| 2                 | `vehicle_type`          | Types of vehicles involved in the accident (e.g., passenger cars, sport utility vehicles, pickup trucks).  |
| 3                 | `rdclass`               | Type of road classification (e.g., local street, state secondary route, public vehicular area).            |
| 4                 | `rdcondition`           | Road condition during the accident (e.g., dry, wet, icy, etc.).                                           |
| 5                 | `lightcond`             | Lighting conditions during the accident (e.g., daylight, dark).                                           |
| 6                 | `ta_date`               | Date the accident occurred (used for filtering by year and month).                                        |
| 7                 | `fatality`              | Indicator of whether the accident involved fatalities (1 = yes, 0 = no).                                   |
| 8                 | `year`                  | Year in which the accident occurred.                                                                      |
| 9                 | `month`                 | Month in which the accident occurred.                                                                     |
| 10                | `day_night`             | Indicator of whether the accident occurred during the day or night.                                       |
| 11                | `Nombre_dia`            | Name of the day (e.g., Monday, Tuesday, etc.).                                                            |
| 12                | `Num_injuries`          | The number of reported injuries (converted to numeric values: 1 for yes, 0 for no).                        |
<h2>4.3. Descriptive Data Analysis</h2>

<p>Once the data was cleaned, several descriptive analyses are performed to generate insights from the data. These analyses are displayed in the dashboard and can be filtered by year (from 2020 to 2024) and month. The following key analyses are implemented:</p>
<ul>
  <li><strong>Number of Fatalities</strong>
    <p>A count of accidents over time, with filters for year and month. To achieve this, it is used a count of the column "tamainid" by month and year.</p>
  </li>

  <li><strong>Number of Fatalities by Vehicle Type</strong>
    <p>A breakdown of accidents by vehicle type (e.g., passenger cars, sport utility vehicles, pickup trucks, etc.).</p>
  </li>

  <li><strong>Number of Fatalities by Road Type</strong>
    <p>Accidents categorized by road type (e.g., local street, state secondary route, public vehicular area).</p>
  </li>

  <li><strong>Number of Fatalities by Road Condition</strong>
    <p>Analysis of accidents by road condition (dry, wet, or other).</p>
  </li>

  <li><strong>Number of Fatalities by Light Conditions</strong>
    <p>A breakdown of accidents that occurred under daylight versus dark lighting conditions.</p>
  </li>
</ul>

<h2>4.4. Dashboard creation</h2>
Besides the graphics for the analysis mention before, it is add 4 new data:  total number of fatalities, total number of injuries, total number of deaths and the day and number with more fatalities (clasified as "Unlucky"). All this data can be filter by month and by year.
<h1>5. Analysis Results</h1>
The total number of fatalities for the 5 years is 19.641, of which the 14% had a report of injuries. The year with more accidents was 2024 with 4.286 fatalities registered, of which 13% had a injurie's report.
In those 5 years died 27 persons.
The day with more accidents in those 5 years was a Friday and the number 14th.
<ul>
  <li><strong>Number of Fatalities</strong>
    <p>For the last 3 years (2022,2023,2024) the month with more accidents was October. For 2020 is January and for 2021 is November</p>
  </li>

  <li><strong>Number of Fatalities by Vehicle Type</strong>
    <p>The vehicule involved in more fatalities is a passenger car. Probably because is the most common car on the roads</p>
  </li>

  <li><strong>Number of Fatalities by Road Type</strong>
    <p>The states secondary routes are the roads with more fatalities registered. A column with the speed of the vehicule o with a description of the accident would have give us more information to understand this phenomeno</p>
  </li>

  <li><strong>Number of Fatalities by Road Condition</strong>
    <p>Apparently, we could think that roads with water are more dangerous, and they are, but study results shows that more accidents are reported in dry road condition. This could happen because we tend to be more attentive and take more care when we know the situation is hazardous, and when we cataloge the situation as a "normal" we tend to relax and rely on it.</p>
  </li>

  <li><strong>Number of Fatalities by Light Conditions</strong>
    <p>Surprisingly more accidents are report with daylight. This could have a similiar answer as the previous commented analysis, we tend to be more distracted when the conditions are good or more favorables to drive, and that's when accidents happend</p>
  </li>
</ul>
<h2>Conclusions</h2>

In conclusion, the analysis reveals that fatalities <strong>are more frequent on dry roads and during daylight hours</strong>, possibly due to drivers' lowered attention when conditions seem favorable. <strong>Passenger cars are the most involved</strong> in fatal accidents, while secondary roads are the most hazardous. <strong>October</strong> consistently emerges as <strong>the month with the highest number of accidents</strong> in the last three years.



