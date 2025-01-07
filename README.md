# Dashboard_Airpollution
This interactive dashboard provides insights into the air quality across various regions in the United States for the year 2024, focusing on the concentrations of CO, NOx, O3 and SO2.

# Input Data
The data used for this analysis comes from the Air Quality System (AQS), focusing on air pollutants <b>Carbon Monoxide (CO), Nitrogen Oxides (NOx), Ozone (O<sub>3</sub>) and Sulfur Dioxide (SO<sub>2</sub>)</b> for the year <b>2024</b>. The dataset contains information on air quality monitoring stations across the United States, with specific details on the geographic location of each station, measurement methods, and pollutant levels. <br>
The raw data can be found in <a href="https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual" target="_blank">United Stated Environmental Protection Agency</a>

The input data has 30 columns, which contain information about:

| Field Position | Field Name         | Description                                                                                             |
|----------------|--------------------|---------------------------------------------------------------------------------------------------------|
| 1              | State Code         | The FIPS code of the state in which the monitor resides.                                                 |
| 2              | County Code        | The FIPS code of the county in which the monitor resides.                                                |
| 3              | Site Number        | A unique number within the county identifying the site.                                                 |
| 4              | Parameter Code     | The AQS code corresponding to the parameter measured by the monitor.                                     |
| 5              | Parameter Name     | The name or description assigned in AQS to the parameter measured by the monitor. Parameters may be pollutants or non-pollutants. |
| 6              | POC                | This is the “Parameter Occurrence Code” used to distinguish different instruments that measure the same parameter at the same site. |
| 7              | Latitude           | The monitoring site’s angular distance north of the equator measured in decimal degrees.               |
| 8              | Longitude          | The monitoring site’s angular distance east of the prime meridian measured in decimal degrees.          |
| 9              | Datum              | The Datum associated with the Latitude and Longitude measures.                                          |
| 10             | First Year of Data | The year in which the earliest sample from this site is available in AQS.                               |
| 11             | Last Sample Date   | The date on which the most recent sample from this site is available in AQS. This is often the best way to determine if a monitor is still operating. Note that the reporting deadlines to AQS are generally lengthy - about 6 months for most parameters. |
| 12             | Monitor Type       | An administrative or regulatory classification for the monitor.                                        |
| 13             | Networks           | A list of the monitoring networks (groups of monitors with common goals and procedures) to which the monitor belongs. If the monitor belongs to more than one network, the names will be separated with semicolons. |
| 14             | Reporting Agency   | The name of the agency responsible for reporting data to AQS.                                           |
| 15             | PQAO               | The name of the Primary Quality Assurance Organization for the monitor. Monitors of the same parameter belonging to the same PQAO must meet aggregate quality assurance requirements. |
| 16             | Collecting Agency  | The name of the agency responsible for collecting data from the monitor.                                 |
| 17             | Exclusions         | If the agency operating the monitor has requested that data from this monitor be excluded from NAAQS calculations and the governing EPA regional office has agreed, the NAAQS standard(s) and the years of exclusion are listed. |
| 18             | Monitoring Objective | Identification of the reason for measuring air quality by the monitor.                                 |
| 19             | Last Method Code   | A three digit code representing the measurement method used by the monitor for its most recent sample (methods can change, but often do not). A method code is only unique within a parameter (that is, method 111 for ozone is not the same as method 111 for benzene). |
| 20             | Last Method        | The full description of the measurement method used by the monitor for its most recent sample (methods can change, but often do not). |
| 21             | NAAQS Primary Monitor | A flag indicating if this monitor is part of a collocated set of monitors at the site and it is the primary data source for NAAQS data comparisons. |
| 22             | QA Primary Monitor | A flag indicating if this monitor is part of a collocated set of monitors at the site and it is the primary monitor for making quality assurance comparisons. |
| 23             | Local Site Name    | The name of the site (if any) given by the State, local, or tribal air pollution control agency that operates it. |
| 24             | Address            | The approximate street address of the monitoring site.                                                  |
| 25             | State Name         | The name of the state where the monitoring site is located.                                             |
| 26             | County Name        | The name of the county where the monitoring site is located.                                            |
| 27             | City Name          | The name of the city where the monitoring site is located. This represents the legal incorporated boundaries of cities and not urban areas. |
| 28             | CBSA Name          | The name of the core bases statistical area (metropolitan area) where the monitoring site is located.  |
| 29             | Tribe Name         | If this monitor resides on tribal lands and the tribe has chosen to identify the site with tribal identifiers, this is the name of the tribe that owns the site. |
| 30             | Extraction Date    | The date on which this data was retrieved from the AQS Data Mart. This does not mean that all data is valid as of this date. Once monitor information is entered by the reporting agency, it may not be updated as values change (e.g., location setting evolves from urban to suburban). |

# Methodology
<p><h2><strong>1. Data Collection:</strong></h2>
After the data is collected and the different analyses to be performed are clearly defined, a data cleaning and transformation process is carried. <br>

The selection of CO, NOx, O<sub>3</sub> and SO<sub>2</sub> as the focus of the analysis is based on their significant impact on air quality and public health. These pollutants are not only commonly monitored but also have well-established regulatory standards, making them critical indicators for assessing air pollution. Here's a brief explanation for each:<br>

NOx (Nitrogen Oxides): Nitrogen oxides, primarily NO and NO2, play a key role in the formation of ground-level ozone and fine particulate matter, both of which have harmful effects on human health and the environment. NOx emissions are primarily from vehicular traffic, industrial sources, and power plants.<br>

CO (Carbon Monoxide): Carbon monoxide is a colorless, odorless gas that is harmful when inhaled in large quantities, especially in poorly ventilated spaces. It is primarily produced by combustion processes, including vehicle emissions and industrial activities. High concentrations of CO can lead to serious health risks, particularly for vulnerable populations.<br>

SO<sub>2</sub> (Sulfur Dioxide): Sulfur dioxide is primarily emitted by industrial processes, particularly the burning of coal and oil in power plants and refineries. SO2 contributes to the formation of acid rain, which can damage ecosystems and structures, and is also a key precursor in the formation of fine particulate matter (PM2.5), which affects respiratory health.<br>

O<sub>3</sub> (Ozone): Ground-level ozone, a secondary pollutant, is a key component of smog. It forms when NOx and volatile organic compounds (VOCs) react in the presence of sunlight. High concentrations of ozone can cause respiratory issues, aggravate asthma, and lead to long-term health problems.<br>

These pollutants were chosen due to their widespread presence, regulatory importance, and significant effects on public health and the environment. By focusing on these pollutants, we can provide valuable insights into air quality trends and inform policies aimed at improving air quality.

However, it has been decided to include the total of the pollutants analyzed in one of the analyses to be performed. This decision is motivated by the desire to gain a holistic view of air quality.</p>

<p><h2><strong>2. Data Cleaning:</strong></h2> 
Before analysis, the dataset is cleaned by checking for missing values, outliers, and inconsistent records. Only valid records are kept for analysis and data completeness and reliability are ensured by removing erroneous entries and handling exceptional event data separately.</p>
<dl>
    <dt>Data understandind and review</dt>
    <db>
        <ul>
            <li>This phase involves thoroughly exploring the dataset to comprehend its structure, contents, and any potential issues that may affect the quality of the analysis. After reviewing the metadata, it is considered necessary to unify the columns of "state code", "county code", "site number", and "parameter code", as the combination of these columns serves as the unique identifier for a monitor.The sum up column is named "id". </li>
> Blockquotes
The formula is in excel to create the column "id" is: =CONCAT([@[State Code]]; "-"; [@[County Code]]; "-"; [@[Site Num]])
            <li>A parameter can be measured more than once at the same monitor, this event is identified with different "POC" values but same "id". This duplicated measures are taken at the same time in the same site and with the same conditions but with diferent physical instruments. In order to eliminate redundancy in these cases, the average of all measurements for the same parameter is calculated, leaving only one measurement per parameter and per station.</li>
        </ul>
    </db>
    <dt>Elimination of duplicated data</dt>
    <db> ------</db>
</dl>
<dl>
    <dt>Relevant columns</dt>
    <db>To perform the proposed analyses, it is concluded that only the information from the following columns will be necessary.
    </db>
</dl>
    <p>

| Column Name                | Description                                                                                                                                  |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| State Name                 | The name of the state where the monitoring site is located.                                                                                 |
| County Name                | The name of the county where the monitoring site is located.                                                                                |
| City Name                  | The name of the city where the monitoring site is located.                                                                                  |
| Latitude                   | The latitude of the monitoring site (in decimal degrees).                                                                                   |
| Longitude                  | The longitude of the monitoring site (in decimal degrees).                                                                                  |
| Parameter Name             | The name or description of the pollutant being measured.                                                                                     |
| Arithmetic Mean            | The average concentration of the pollutant for the year.                                                                                    |
| 1st Max Value              | The highest value of the pollutant concentration in the year.                                                                                |
| 2nd Max Value              | The second highest value of the pollutant concentration.                                                                                     |
| 3rd Max Value              | The third highest value of the pollutant concentration.                                                                                      |
| 4th Max Value              | The fourth highest value of the pollutant concentration.                                                                                     |
| Primary Exceedance Count   | The count of exceedances of primary air quality standards.                                                                                   |
| Secondary Exceedance Count | The count of exceedances of secondary air quality standards.                                                                                 |
| Observation Percent        | The percentage of valid observations compared to the expected.                                                                               |
| Completeness Indicator     | Indicates if the data meets the required completeness criteria.                                                                              |
| Event Type                 | Type of exceptional event (if any) that affected data.                                                                                      |
| Exceptional Data Count     | The number of data points impacted by exceptional events.                                                                                   |
| Num Obs Below MDL          | The number of observations below the method detection limit.                                                                                 |
    </p>

<p><h2><strong>3. Data Analysis</strong></h2> Several analyses were conducted to understand air quality patterns in 2024. These include:</p>
<ul>
    <li>Mapping pollutant distribution using latitude, longitude, and pollutant concentrations.</li>
    <li>Comparing pollutant concentrations between different states, counties, and cities.</li>
    <li>Identifying sites with the highest and lowest pollution levels.</li>
    <li>Evaluating exceedances of air quality standards, both primary and secondary.</li>
    <li>Investigating the impact of exceptional events (e.g., wildfires) on air quality.</li>
    <li>Analyzing the distribution of pollutant concentrations through descriptive statistics.</li>
    <li>Evaluating the coverage and completeness of monitoring data.</li>
    <li>Assessing data quality based on observations below the method detection limit.</li>
    <li>Identifying the most frequently measured pollutants in 2024.</li>
</ul>

<p><strong>Visualization:</strong> Interactive maps, bar graphs, and box plots were used to visualize the results of the analysis. These visualizations helped in identifying geographic patterns, comparing pollutant levels, and evaluating air quality trends throughout the year.</p>

<p><strong>Statistical Methods:</strong> Statistical techniques such as mean, standard deviation, and percentiles were used to summarize pollutant concentrations. Box plots and heat maps were generated to explore the distribution and variation in air quality data. In addition, correlation analysis was conducted to understand relationships between different pollutants and their geographic spread.</p>

<p><strong>Conclusion:</strong> The methodology provided a comprehensive approach to evaluating air quality data for 2024, offering insights into regional pollution levels, compliance with air quality standards, and the impact of exceptional events. The results can help policymakers and researchers prioritize areas in need of air quality improvements and address any data quality issues observed during the monitoring process.</p>

# Resultados
<h2>1. Map of Pollutant Distribution in 2024</h2>
<p><strong>Analysis:</strong> Visualize the average concentrations of pollutants across various geographic locations (latitude, longitude, state, city). A heatmap will help identify areas with higher pollutant levels, such as PM2.5, NO2, CO, etc., during 2024.</p>

<h2>2. Comparison of Pollutants Between States, Counties, and Cities</h2>
<p><strong>Analysis:</strong> Compare the average levels of CO, NOx, O<sub>3</sub> and SO<sub>2</sub> pollutant concentrations in various locations, including states, counties, and cities. This will reveal areas with higher or lower pollution levels, providing insights into the regional pollution patterns for 2024.</p>

<h2>3. Identification of Sites with the Highest and Lowest Pollution in 2024</h2>
<p><strong>Analysis:</strong> Identify the monitoring sites with the highest and lowest CO, NOx, O<sub>3</sub> and SO<sub>2</sub> pollutant concentrations in 2024. This can pinpoint areas that need immediate attention due to high pollution levels.</p>

<h2>4. Exceedance of Air Quality Standards in 2024</h2>
<p><strong>Analysis:</strong> Analyze how often  CO, NOx, O<sub>3</sub> and SO<sub>2</sub> pollutant levels exceeded air quality standards in 2024. It will identify regions where pollutants surpassed primary or secondary air quality thresholds, indicating non-compliance with air quality regulations.</p>

<h2>5. Analysis of Exceptional Events in 2024</h2>
<p><strong>Analysis:</strong> Investigate the impact of exceptional events (e.g., wildfires) on air quality in 2024. This analysis will highlight which sites were affected by these events and the extent to which air quality data was influenced.</p>

<h2>6. Distribution of Pollutant Concentrations</h2>
<p><strong>Analysis:</strong> Analyze the distribution of CO, NOx, O<sub>3</sub> and SO<sub>2</sub> concentrations, focusing on the maximum recorded values. This will help determine whether pollution levels were sporadic or consistent throughout the year.</p>

<h2>7. Coverage of Monitoring Data in 2024</h2>
<p><strong>Analysis:</strong> Assess the coverage and completeness of air quality monitoring data in 2024. This will identify areas with missing or unreliable data, ensuring the accuracy of the dataset and its applicability to the analyses.</p>

<h2>8. Data Quality Evaluation in 2024</h2>
<p><strong>Analysis:</strong> Evaluate the number of observations below the method detection limit (MDL). This will help detect potential issues with monitoring equipment or data collection, ensuring the quality of the air quality data.</p>

<h2>9. Analysis of the Most Measured Parameters in 2024</h2>
<p><strong>Analysis:</strong> Identify the most frequently measured pollutants in 2024. This will help prioritize attention on the pollutants that are most commonly monitored, guiding future research or regulatory actions based on observed patterns.This is the only part of the global analysis that takes into account all the pollutants being analyzed. </p>

# Discussions
''' Desarrollar todas las ideas que has ido generando durante el trabajo y comparacion con otros estudios. Limitaciones con las que se ha topado el estudio '''

# Conclusiones

''' Recapitulacion de los objetivos del trabajo y las ideas que has sacado '''


