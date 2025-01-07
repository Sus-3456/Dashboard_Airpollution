# Dashboard_Airpollution
This interactive dashboard provides insights into the air quality across various regions in the United States for the year 2024, focusing on the concentrations of CO, NOx, O3 and SO2.

# Input Data
The data used for this analysis comes from the Air Quality System (AQS), focusing on air pollutants <b>Carbon Monoxide (CO), Nitrogen Oxides (NOx), Ozone (O<sub>3</sub>) and Sulfur Dioxide (SO<sub>2</sub>)</b> for the year <b>2024</b>. The dataset contains information on air quality monitoring stations across the United States, with specific details on the geographic location of each station, measurement methods, and pollutant levels. <br>
The raw data can be found in <a href="https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual" target="_blank">United Stated Environmental Protection Agency</a>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Monitoring Data Table</title>
    <style>
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            padding: 8px;
            border: 1px solid #ddd;
            text-align: left;
        }
        th {
            background-color: #f2f2f2;
        }
    </style>
</head>
<body>

    <h2>Monitoring Data Table</h2>

    <table>
        <thead>
            <tr>
                <th>Field Position</th>
                <th>Field Name</th>
                <th>Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>State Code</td>
                <td>The FIPS code of the state in which the monitor resides.</td>
            </tr>
            <tr>
                <td>2</td>
                <td>County Code</td>
                <td>The FIPS code of the county in which the monitor resides.</td>
            </tr>
            <tr>
                <td>3</td>
                <td>Site Number</td>
                <td>A unique number within the county identifying the site.</td>
            </tr>
            <tr>
                <td>4</td>
                <td>Parameter Code</td>
                <td>The AQS code corresponding to the parameter measured by the monitor.</td>
            </tr>
            <tr>
                <td>5</td>
                <td>Parameter Name</td>
                <td>The name or description assigned in AQS to the parameter measured by the monitor. Parameters may be pollutants or non-pollutants.</td>
            </tr>
            <tr>
                <td>6</td>
                <td>POC</td>
                <td>This is the “Parameter Occurrence Code” used to distinguish different instruments that measure the same parameter at the same site.</td>
            </tr>
            <tr>
                <td>7</td>
                <td>Latitude</td>
                <td>The monitoring site’s angular distance north of the equator measured in decimal degrees.</td>
            </tr>
            <tr>
                <td>8</td>
                <td>Longitude</td>
                <td>The monitoring site’s angular distance east of the prime meridian measured in decimal degrees.</td>
            </tr>
            <tr>
                <td>9</td>
                <td>Datum</td>
                <td>The Datum associated with the Latitude and Longitude measures.</td>
            </tr>
            <tr>
                <td>10</td>
                <td>First Year of Data</td>
                <td>The year in which the earliest sample from this site is available in AQS.</td>
            </tr>
            <tr>
                <td>11</td>
                <td>Last Sample Date</td>
                <td>The date on which the most recent sample from this site is available in AQS. This is often the best way to determine if a monitor is still operating. Note that the reporting deadlines to AQS are generally lengthy - about 6 months for most parameters.</td>
            </tr>
            <tr>
                <td>12</td>
                <td>Monitor Type</td>
                <td>An administrative or regulatory classification for the monitor.</td>
            </tr>
            <tr>
                <td>13</td>
                <td>Networks</td>
                <td>A list of the monitoring networks (groups of monitors with common goals and procedures) to which the monitor belongs. If the monitor belongs to more than one network, the names will be separated with semicolons.</td>
            </tr>
            <tr>
                <td>14</td>
                <td>Reporting Agency</td>
                <td>The name of the agency responsible for reporting data to AQS.</td>
            </tr>
            <tr>
                <td>15</td>
                <td>PQAO</td>
                <td>The name of the Primary Quality Assurance Organization for the monitor. Monitors of the same parameter belonging to the same PQAO must meet aggregate quality assurance requirements.</td>
            </tr>
            <tr>
                <td>16</td>
                <td>Collecting Agency</td>
                <td>The name of the agency responsible for collecting data from the monitor.</td>
            </tr>
            <tr>
                <td>17</td>
                <td>Exclusions</td>
                <td>If the agency operating the monitor has requested that data from this monitor be excluded from NAAQS calculations and the governing EPA regional office has agreed, the NAAQS standard(s) and the years of exclusion are listed.</td>
            </tr>
            <tr>
                <td>18</td>
                <td>Monitoring Objective</td>
                <td>Identification of the reason for measuring air quality by the monitor.</td>
            </tr>
            <tr>
                <td>19</td>
                <td>Last Method Code</td>
                <td>A three digit code representing the measurement method used by the monitor for its most recent sample (methods can change, but often do not). A method code is only unique within a parameter (that is, method 111 for ozone is not the same as method 111 for benzene).</td>
            </tr>
            <tr>
                <td>20</td>
                <td>Last Method</td>
                <td>The full description of the measurement method used by the monitor for its most recent sample (methods can change, but often do not).</td>
            </tr>
            <tr>
                <td>21</td>
                <td>NAAQS Primary Monitor</td>
                <td>A flag indicating if this monitor is part of a collocated set of monitors at the site and it is the primary data source for NAAQS data comparisons.</td>
            </tr>
            <tr>
                <td>22</td>
                <td>QA Primary Monitor</td>
                <td>A flag indicating if this monitor is part of a collocated set of monitors at the site and it is the primary monitor for making quality assurance comparisons.</td>
            </tr>
            <tr>
                <td>23</td>
                <td>Local Site Name</td>
                <td>The name of the site (if any) given by the State, local, or tribal air pollution control agency that operates it.</td>
            </tr>
            <tr>
                <td>24</td>
                <td>Address</td>
                <td>The approximate street address of the monitoring site.</td>
            </tr>
            <tr>
                <td>25</td>
                <td>State Name</td>
                <td>The name of the state where the monitoring site is located.</td>
            </tr>
            <tr>
                <td>26</td>
                <td>County Name</td>
                <td>The name of the county where the monitoring site is located.</td>
            </tr>
            <tr>
                <td>27</td>
                <td>City Name</td>
                <td>The name of the city where the monitoring site is located. This represents the legal incorporated boundaries of cities and not urban areas.</td>
            </tr>
            <tr>
                <td>28</td>
                <td>CBSA Name</td>
                <td>The name of the core bases statistical area (metropolitan area) where the monitoring site is located.</td>
            </tr>
            <tr>
                <td>29</td>
                <td>Tribe Name</td>
                <td>If this monitor resides on tribal lands and the tribe has chosen to identify the site with tribal identifiers, this is the name of the tribe that owns the site.</td>
            </tr>
            <tr>
                <td>30</td>
                <td>Extraction Date</td>
                <td>The date on which this data was retrieved from the AQS Data Mart. This does not mean that all data is valid as of this date. Once monitor information is entered by the reporting agency, it may not be updated as values change (e.g., location setting evolves from urban to suburban).</td>
            </tr>
        </tbody>
    </table>

</body>
</html>

