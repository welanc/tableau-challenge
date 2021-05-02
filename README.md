# Tableau Challenge: Data Analysis of Citi Bike Data for New York

This tableau challenge explores the ridership data and usage patterns of the New York Citi Bike system. The visualisation can be found here: [https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/STORYNewYorkCitiBikeRidershipAnalysis](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/STORYNewYorkCitiBikeRidershipAnalysis)

Contributors: Welan Chu


# Data Wrangling

~~Our working files, resources and outputs can be found in the following structure:~~
 
## Citi Bike website

The dataset used can be found at the [Citi Bike system data](https://www.citibikenyc.com/system-data) website:
 - **[Full dataset:](https://s3.amazonaws.com/tripdata/index.html)** every publicly available date.
 - **[February 2014:](https://s3.amazonaws.com/tripdata/201402-citibike-tripdata.zip)** direct link to February 2014 dataset used in this analysis.
 - **[August 2014:](https://s3.amazonaws.com/tripdata/201408-citibike-tripdata.zip)** direct link to August 2014 dataset used in this analysis.
 - **[February 2019:](https://s3.amazonaws.com/tripdata/201902-citibike-tripdata.csv.zip)** direct link to February 2019 dataset used in this analysis.
 - **[August 2019:](https://s3.amazonaws.com/tripdata/201908-citibike-tripdata.csv.zip)** direct link to August 2019 dataset used in this analysis.

## Python & Jupyter Notebook

The data directory contains a Jupyter Notebook used to extract and transform the raw Citi Bike CSV data. Note, the CSV files were located in a directory titled "unzipped" which is not included in this repository. Please download the required CSV files from the links above under the heading "Citi Bike website." 

### Extracting and transforming the data

Each CSV was imported as individual Pandas DataFrames and checked for consistency between datasets (i.e. series headers).

Due to the extremely large datasets, it was decided to reduce the data to only one week per month (from the 7th to the 14th, excluding the 14th). These dates were chosen to best represent a typical week in that month and season as there appear to be no significant public holidays that would affect rider behaviour. A function `week_data()` was created to filter each dataset accordingly.

The four DataFrames were then concatenated using `pd.concat()` to create a single DataFrame for export and load in Tableau.

**Note:** During the visualisation process, it was found that in order to map start and end locations for the Tableau Visualisation *"Rides Map"* (refer to section: **Rides Map** in **Tableau > Visualisations**) the data needed to have a single series each for latitude, longitude, and a column to act as an ID. This was accomplished by duplicating the DataFrame rows, filling a new "latitude" series with the start station latitude in the original row and the end station latitude in the duplicate row, doing the same thing for a new "longitude" series, and creating an "ID" series that concatenated the start station and end station names, and filled in the original and duplicate row, which identifies the two rows as a corresponding pair. Further reading on this method can be found [here](https://help.tableau.com/current/pro/desktop/en-us/maps_howto_origin_destination.htm#Origin). In order to prevent duplicated data in every other series, the duplicated rows were isolated using the `.loc()` method and cells set to `None`, thus avoiding inadvertent double counting.  

****

# Tableau

The tableau visualisations can be found here: [https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/STORYNewYorkCitiBikeRidershipAnalysis](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/STORYNewYorkCitiBikeRidershipAnalysis)  

For analysis of the two phenomena discovered in the dataset, please refer to the annotations within the Tableau Visualisation Story.
 
## Table of Contents:

 - **Visualisations:**
	 - [Rides Map](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/RidesMap)
	-   [Trip Duration vs Age & Gender 2014](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/TripDurationvsAgeGender2014)
	-   [Trip Duration vs Age & Gender 2019](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/TripDurationvsAgeGender2019)
	-   [Total Start Station Popularity](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/TotalStartStationPopularity)
	-   [Station Popularity Over Winter 2014](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/StationPopularityOverWinter2014)
	-   [Station Popularity Over Summer 2014](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/StationPopularityOverSummer2014)
	-   [Station Popularity Over Winter 2019](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/StationPopularityOverWinter2019)
	-   [Station Popularity Over Summer 2019](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/StationPopularityOverSummer2019)
	-   [Ridership Per Hour Over Summer / Winter](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/RidershipPerHourOverSummerWinter)
	-   [Ridership Per Hour Per Gender](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/RidershipPerHourPerGender)
	-   [Ridership Per Hour Over Winter](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/RidershipPerHourOverWinter)
	-   [Ridership Per Hour Over Summer](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/RidershipPerHourOverSummer)
	-   [Total Ridership Per Hour Summer & Winter](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/TotalRidershipPerHourSummerWinter)
- **Dashboards:**
	-   [[DASHBOARD] Popular Stations Over Winter](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/DASHBOARDPopularStationsOverWinter)
	-   [[DASHBOARD] Popular Stations Over Summer](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/DASHBOARDPopularStationsOverSummer)
	-   [[DASHBOARD] Ridership Change by Age and Gender 2014](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/DASHBOARDRidershipChangebyAgeandGender2014)
	-   [[DASHBOARD] Ridership Change by Age and Gender 2019](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/DASHBOARDRidershipChangebyAgeandGender2019)
	-   [[DASHBOARD] Ridership Per Hour](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/DASHBOARDRidershipPerHour)
- **Story:**
	-   [[STORY] New York Citi Bike Ridership Analysis](https://public.tableau.com/profile/welan/tableau-challenge#!/vizhome/tableau-challenge_16192674354000/STORYNewYorkCitiBikeRidershipAnalysis)

## Visualisations
### City Official Maps:
- **Rides Map:** map showing each station and the most frequented routes per station over the four weeks analysed.
- **Station Popularity Over Winter 2014:** dynamic map that shows how each station's popularity changes over time by day (in map) and by year (comparison with 2019 map.)
- **Station Popularity Over Winter 2019:** dynamic map that shows how each station's popularity changes over time by day (in map) and by year (comparison with 2014 map.) 
- **Station Popularity Over Summer 2014:** dynamic map that shows how each station's popularity changes over time by day (in map) and by year (comparison with 2019 map.)
- **Station Popularity Over Summer 2019:** dynamic map that shows how each station's popularity changes over time by day (in map) and by year (comparison with 2014 map.) 
- **Total Start Station Popularity:** map of aggregated data of every station and the number of rides started at each location.

### Phenomena One: Age and Gender
- **Trip Duration vs Age & Gender 2014:** stacked bar chart comparing average trip duration in minutes and number of riders per rider age. 
- **Trip Duration vs Age & Gender 2019:** stacked bar chart comparing average trip duration in minutes and number of riders per rider age.


### Phenomena Two: Hourly Difference
- **Ridership Per Hour Over Summer/Winter:** line chart of
- **Ridership Per Hour Per Gender:** stacked line chart of average ridership over 7 days in February/August of 2014/2019, measured per gender. 
- **Ridership Per Hour Over Summer:** bar chart of total rides per hour (both genders) comparing 2014 ridership to 2019 ridership over summer (August.)
- **Ridership Per Hour Over Winter:** bar chart of total rides per hour (both genders) comparing 2014 ridership to 2019 ridership over winter (February.)
- **Total Ridership Per Hour Summer & Winter:** (unused) visualisation filtered by age, showing most popular hours for using the service for that age group.  

## Dashboards
- **Popular Stations Over Winter:** Interactive maps with sliding scales to analyse number of rides started at each location per day(s); one map for 2014 and one for 2019 for visual comparison.
- **Popular Stations Over Summer:** Interactive maps with sliding scales to analyse number of rides started at each location per day(s); one map for 2014 and one for 2019 for visual comparison.
- **Ridership Change by Age and Gender 2014:** Combination of map visualisation and stacked bar chart of relevant time periods. Clicking the map to a single station will filter the stacked bar chart to present the data for that station.
- **Ridership Change by Age and Gender 2019:** Combination of map visualisation and stacked bar chart of relevant time periods. Clicking the map to a single station will filter the stacked bar chart to present the data for that station.
- **Ridership Per Hour:** Combination of aggregated line chart analysing average ridership in February/August of 2014/2019 and side-by-side bar charts displaying the same data but separated by month to isolate summer and winter analyses.

## Story
### New York Citi Bike Ridership Analysis**
	
- **Slide 1:** Where do riders most finish from each starting station?frequently
- **Slide 2:** How has ridership changed in winter from 2014 to 2019
- **Slide 3:** How has ridership changed in summer from 2014 to 2019
- **Slide 4:** Ridership changes per hour between summer vs winter, 2014 & 2019
- **Slide 5:** Ridership by age and gender (M/F) in 2014 summer vs. winter
- **Slide 6:** Ridership by age and gender (M/F) in 2019 summer vs. winter# tableau-challenge