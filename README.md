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
   <li><dt>Three new time-related columns were created:</dt>
      <dd>one for the month in which the accident occurred, another for the day, and another for the day of the week.</dd>
      <blockquote>Formula use to "Dia" column: =TEXTO([@[ta_date]]; "dddd")</blockquote>
      <blockquote>Formula use to "Num_dia" column: =[@DIA]</blockquote>
      <blockquote>Formula use to "Nom_Mes" column: =ELEGIR([@month]; "Enero"; "Febrero"; "Marzo"; "Abril"; "Mayo"; "Junio"; "Julio"; "Agosto"; "Septiembre"; "Octubre"; "Noviembre"; "Diciembre")</blockquote>
   </li>

   <li><dt>A new column was created to categorize the lightcond column into two categories:</dt>
      <dd>The raw column had 5 categories, in which there were two with no usable data "OTHER" and "UNKNOWN". Those two categories are not considered for the analysis. The rest of the categories were classified into "daylight" or "darkness".</dd>
   </li>

   <li><dt>A new column was created to convert the values in the injuries column into numeric values:</dt>
      <dd>The values with "Yes" are changed into "1" and the values with "No" are changed into "0".</dd>
      <blockquote>Formula use in column "Num_injuries": =SI([@injuries]="yes"; 1; 0)</blockquote>
   </li>

   <li><dt>The vehicle_type column was simplified to a one or two-word description:</dt>
      <dd>the column originally contained two or three brief descriptions separated by commas, and the new column now retains only the first description.</dd>
      <blockquote>Formula use for vehicle: =LEFT([@vehicule_type]; FIND(","; [@vehicule_type] )-1)</blockquote>
   </li>

   <li><dt>The rdcondition column was simplified:</dt>
      <dd>The new categories are: "dry", "wet", or "other".</dd>
   </li>

   <li><dt>Blank spaces in the columns:</dt>
      <dd>vehicle_type, rdsurface, rdcondition, and weather were filled.</dd>
      <blockquote>Using filter by "Blank" and then putting "OTHER" in the columns left</blockquote>
   </li>

   <li><dt>Data related to 2025 was removed due to being incomplete.</dt></li>
   
   <li><dt>A new column was created to categorize the lightcond column into two categories:</dt>
      <dd>The raw column had 5 categories, in which there were two with no usable data "OTHER" and "UNKNOWN". Those two categories are not considered to the analysis. The rest of the categories were classified into "daylight" or "darkness".</dd>
      <blockquote>Formula use for "day_night" column: =SI(ESNUMERO(ENCONTRAR("DAYLIGHT";[@lightcond])); "DAYLIGHT"; "DARK")</blockquote>
   </li>
</ul>

<h2>4.2. Removing Duplicates</h2>
<h3>4.3. Descriptive Analysis</h3>
<h3>4.4. Dashboard creation</h3>
<h2>5. Analysis Results</h2>
<h2>Conclusions</h2>

1. **Vehicle Type Normalization**:  
   The `vehicle_type` column originally contained multiple vehicle types separated by a comma. I simplified this to include only the first vehicle type in each record.  
   **Formula used**:  
   ```excel
   =LEFT(H1,FIND(",",H1)-1)



