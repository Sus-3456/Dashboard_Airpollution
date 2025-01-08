# Dashboard_Airpollution
This interactive dashboard provides insights into the air quality across various regions in the United States for the year 2024, focusing on the concentrations of CO, NOx, O3 and SO2.

# Input Data
The data used for this analysis comes from the Air Quality System (AQS), focusing on air pollutants <b>Carbon Monoxide (CO), Nitrogen Oxides (NOx), Ozone (O<sub>3</sub>) and Sulfur Dioxide (SO<sub>2</sub>)</b> for the year <b>2024</b>. The dataset contains information on air quality monitoring stations across the United States, with specific details on the geographic location of each station, measurement methods, and pollutant levels. <br>
The raw data can be found in <a href="https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual" target="_blank">United Stated Environmental Protection Agency</a>

The input data has 55 columns, which contain information about:

| **Field Position** | **Field Name**           | **Description**                                                                                                                                         |
|--------------------|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1                  | State Code               | The FIPS code of the state in which the monitor resides.                                                                                                |
| 2                  | County Code              | The FIPS code of the county in which the monitor resides.                                                                                               |
| 3                  | Site Num                 | A unique number within the county identifying the site.                                                                                               |
| 4                  | Parameter Code           | The AQS code corresponding to the parameter measured by the monitor.                                                                                   |
| 5                  | POC                      | The “Parameter Occurrence Code” used to distinguish different instruments measuring the same parameter at the same site.                                |
| 6                  | Latitude                 | The monitoring site’s angular distance north of the equator in decimal degrees.                                                                       |
| 7                  | Longitude                | The monitoring site’s angular distance east of the prime meridian in decimal degrees.                                                                  |
| 8                  | Datum                    | The Datum associated with the Latitude and Longitude measures.                                                                                         |
| 9                  | Parameter Name           | The name or description assigned in AQS to the parameter measured by the monitor.                                                                     |
| 10                 | Sample Duration          | The length of time air passes through the monitoring device before it is analyzed (e.g., 24-hour sample).                                               |
| 11                 | Pollutant Standard       | The ambient air quality standard rules used to aggregate statistics.                                                                                  |
| 12                 | Metric Used              | The base metric used in the calculation of aggregate statistics (e.g., Daily Maximum).                                                                |
| 13                 | Method Name              | A description of the processes, equipment, and protocols used to gather and measure the sample.                                                        |
| 14                 | Year                     | The year the annual summary data represents.                                                                                                           |
| 15                 | Units of Measure         | The unit of measure for the parameter (converted to standard units for calculations).                                                                  |
| 16                 | Event Type               | Indicates if data measured during exceptional events (e.g., wildfires) is included or excluded from the summary.                                        |
| 17                 | Observation Count        | The number of observations (samples) taken during the year.                                                                                           |
| 18                 | Observation Percent      | The percentage of valid observations compared to the number of scheduled observations.                                                                 |
| 19                 | Completeness Indicator   | Indicates if the regulatory data completeness criteria have been met (Y = yes, N = no).                                                               |
| 20                 | Valid Day Count          | The number of valid days during the year based on monitoring criteria.                                                                                 |
| 21                 | Required Day Count       | The number of days the monitor was scheduled to take samples.                                                                                          |
| 22                 | Exceptional Data Count   | The number of data points affected by exceptional air quality events.                                                                                 |
| 23                 | Null Data Count          | The number of scheduled samples where no data was collected and the reason for the absence.                                                           |
| 24                 | Primary Exceedance Count | The number of samples exceeding the primary air quality standard.                                                                                     |
| 25                 | Secondary Exceedance Count| The number of samples exceeding the secondary air quality standard.                                                                                  |
| 26                 | Certification Indicator   | Indicates if the data’s completeness and accuracy have been certified (Certified, Uncertified, etc.).                                                  |
| 27                 | Num Obs Below MDL        | The number of samples below the method detection limit (MDL) for the monitoring instrument.                                                           |
| 28                 | Arithmetic Mean          | The average (arithmetic mean) value for the year.                                                                                                      |
| 29                 | Arithmetic Standard Dev  | The standard deviation about the mean of the values for the year.                                                                                     |
| 30                 | 1st Max Value            | The highest value for the year.                                                                                                                         |
| 31                 | 1st Max DateTime         | The date and time when the highest value for the year occurred.                                                                                        |
| 32                 | 2nd Max Value            | The second highest value for the year.                                                                                                                 |
| 33                 | 2nd Max DateTime         | The date and time when the second highest value occurred.                                                                                             |
| 34                 | 3rd Max Value            | The third highest value for the year.                                                                                                                  |
| 35                 | 3rd Max DateTime         | The date and time when the third highest value occurred.                                                                                              |
| 36                 | 4th Max Value            | The fourth highest value for the year.                                                                                                                 |
| 37                 | 4th Max DateTime         | The date and time when the fourth highest value occurred.                                                                                             |
| 38                 | 1st Max Non Overlapping Value | The highest value for 8-hour CO averages.                                                                                                           |
| 39                 | 1st NO Max DateTime      | The date and time when the first maximum non-overlapping value occurred.                                                                               |
| 40                 | 2nd Max Non Overlapping Value | The second highest non-overlapping value for 8-hour CO averages.                                                                                     |
| 41                 | 2nd NO Max DateTime      | The date and time when the second maximum non-overlapping value occurred.                                                                              |
| 42                 | 99th Percentile          | The value where 99% of the rest of the values are equal to or less than.                                                                                |
| 43                 | 98th Percentile          | The value where 98% of the values are equal to or less than.                                                                                          |
| 44                 | 95th Percentile          | The value where 95% of the values are equal to or less than.                                                                                          |
| 45                 | 90th Percentile          | The value where 90% of the values are equal to or less than.                                                                                          |
| 46                 | 75th Percentile          | The value where 75% of the values are equal to or less than.                                                                                          |
| 47                 | 50th Percentile          | The median value, where 50% of the values are equal to or less than.                                                                                  |
| 48                 | 10th Percentile          | The value where 10% of the values are equal to or less than.                                                                                          |
| 49                 | Local Site Name          | The name of the site provided by the air pollution control agency.                                                                                   |
| 50                 | Address                  | The approximate street address of the monitoring site.                                                                                               |
| 51                 | State Name               | The name of the state where the monitoring site is located.                                                                                           |
| 52                 | County Name              | The name of the county where the monitoring site is located.                                                                                          |
| 53                 | City Name                | The name of the city where the monitoring site is located.                                                                                            |
| 54                 | CBSA Name                | The name of the core-based statistical area (metropolitan area) where the monitoring site is located.                                                  |
| 55                 | Date of Last Change      | The date the last update of any numeric values in the record was made in the AQS data system.                                                          |



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
<blockquote>The formula use in excel to create the column "id" is: =CONCAT([@[State Code]]; "-"; [@[County Code]]; "-"; [@[Site Num]]; "-"; [@[Parameter Code]])</blockquote>
            <li> The "Null Data Count" column shows how many samples were expected but not recorded, providing insight into the reliability or interruptions in the data collection process. Therefore, rows with a value greater than 0 in this column will be removed, as the data they provide is not valid.</li>
            <blockquote>Select the column, filter by "value is not equal to: 0"  and eliminate all the rows that appears.</blockquote>
            <li>The "Completeness Indicator" column shows how many samples meet the criteria. Rows with value "N" will be removed, as the data provid is not meeting the criteria.</li>
            <blockquote>Select the column, filter by value "N" and eliminate all the rows that appears.</blockquote>
            <li>A parameter can be measured more than once at the same monitor, this event is identified with different "POC" values but same "id". This duplicated measures are taken at the same time in the same site and with the same conditions but with diferent physical instruments. In order to eliminate redundancy in these cases, the average of all measurements for the same parameter is calculated, leaving only one measurement per parameter and per station.</li>
            <li>Since all the data is collected in the year 2024, it has been decided to remove the "year" column. The columns "- Max Datetime" include both the date and the time when the data was recorded. It has been decided to split this information into two separate columns: one for "max date" and another for "max time" in order to make the information more accessible and reachable.</li>
<blockquote>First we create two new columns, one with "Date" format and the other with "Time". Afterward, we put this formula in "Date": =ENTERO([@[1st Max DateTime]]) ; and this other formula in "Time": =[@[1st Max DateTime]] - ENTERO([@[1st Max DateTime]])</blockquote>
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


