## [**IS843_BigDataProject**](https://www.canva.com/design/DAFhCuOYQP8/7eZBLY77U9Weroa-09ce4w/view?utm_content=DAFhCuOYQP8&utm_campaign=designshare&utm_medium=link&utm_source=publishsharelink)


# [**Analyzing NYC Taxi Trips: Understanding Demand and Optimizing Revenue**](https://www.canva.com/design/DAFhCuOYQP8/7eZBLY77U9Weroa-09ce4w/view?utm_content=DAFhCuOYQP8&utm_campaign=designshare&utm_medium=link&utm_source=publishsharelink)


## IS843 - Team 6

- Gabriela Vargas Horle
- Harshil Thakkar
- Heijang Wu
- Priyank Negi
- Wenxuan Yan

## 1. Introduction

### Project objective:

Our exploration will enable us to identify taxi trip patterns in NYC and develop strategies accordingly to improve revenue for taxi drivers and taxi companies.

We combined datasets from 2018 to 2021 to draw more insight from our analysis. As data from 2020 onwards show the impact of the pandemic on taxi demand, providing information from the two years prior to the pandemic would lead to a more accurate interpretation of results.

For Phase 1 of our project we explored the data to understand commonalities in demand, depending on year, month, day of the week, time of the day and location. In Phase 2 we utilized our findings to discern further how those factors affect revenue.

### Motivation:

Taxi market has been facing great competition in recent years, as an increasing number of people switch from taxi to share-riding, such as Uber and Lyft, as a means of transportation. While taxi companies and drivers may have a hard time going through this transition, there are people who prefer and need to take taxis. By analyzing taxi trip patterns in NYC, we will help taxi companies and drivers learn more about the customers they're serving and, more importantly, how to increase revenue to stay in business.

The analysis revealed that taxi trips were most popular during the morning and afternoon hours. Short-distance trips were the most popular, with the most frequently traveled routes being in the upper east and upper west side, spanning 66 blocks. Long trips were found to be the most expensive per minute. In terms of difference in demand based on the day of the week; Friday has the highest demand, while Sunday has the lowest.

### Report Summary:

We cleaned the dataframe to exclude unrepresentative data points and created features that better fit the purpose of our analyses. We conducted exploratory data analysis on taxi trip demand patterns, revenue patterns, and how they interrelate to one another. We also implemented machine learning methods, including linear regression, random forest, and GBT regression, to predict taxi trip price based on other features.

## 2. Data source

### Data Source:

The datasets used were downloaded from BigQuery. The information in this dataset was made available by the New York City Taxi and Limousine Commission (TLC).

This project used datasets containing data regarding yellow taxi trips in New York City spanning from 2018 to 2021. We also used a taxi zone dataset to assign name locations to the zone_ids, which by itself, would not sufficiently contextualize the data.

We decided not to include data from 2022 as early exploration of that dataset indicated that values from the month of December were missing from the original dataset featured on BigQuery.

### Data dictionary

**taxi_zone_geom**

bigquery-public-data.new_york_taxi_trips.taxi_zone_geom

| Column Name | Description | Type |
|-------------|-------------|------|
| zone_id | Unique ID number of each taxi zone. Corresponds with the pickup_location_id and dropoff_location_id in each of the trips tables | STRING |
| zone_name | Full text name of the taxi zone | STRING |
| borough | Borough containing the taxi zone | STRING |
| zone_geom | Geometric outline that defines the taxi zone suitable for GIS analysis. | GEOGRAPHY |

**TLC Yellow Trips Dataset**

The TLC Yellow Trips Dataset contains data on taxi trips in New York City using yellow taxis, as reported to the New York City Taxi and Limousine Commission (TLC) for the years 2018-2021. The data is stored in Google BigQuery and can be accessed via the following table names:

- 2018: `bigquery-public-data.new_york_taxi_trips.tlc_yellow_trips_2018`
- 2019: `bigquery-public-data.new_york_taxi_trips.tlc_yellow_trips_2019`
- 2020: `bigquery-public-data.new_york_taxi_trips.tlc_yellow_trips_2020`
- 2021: `bigquery-public-data.new_york_taxi_trips.tlc_yellow_trips_2021`

## Data Description

The dataset contains the following columns:

- `vendor_id`: A code indicating the LPEP provider that provided the record. 1= Creative Mobile Technologies, LLC; 2= VeriFone Inc.
- `pickup_datetime`: The date and time when the meter was engaged.
- `dropoff_datetime`: The date and time when the meter was disengaged.
- `passenger_count`: The number of passengers in the vehicle. This is a driver-entered value.
- `trip_distance`: The elapsed trip distance in miles reported by the taximeter.
- `rate_code`: The final rate code in effect at the end of the trip. 1= Standard rate 2=JFK 3=Newark 4=Nassau or Westchester 5=Negotiated fare 6=Group ride
- `store_and_fwd_flag`: This flag indicates whether the trip record was held in vehicle memory before sending to the vendor, aka 'store and forward,' because the vehicle did not have a connection to the server. Y= store and forward trip N= not a store and forward trip
- `payment_type`: A numeric code signifying how the passenger paid for the trip. 1= Credit card 2= Cash 3= No charge 4= Dispute 5= Unknown 6= Voided trip
- `fare_amount`: The time-and-distance fare calculated by the meter.
- `extra`: Miscellaneous extras and surcharges. Currently, this only includes the 0.50 and 1 dollar rush hour and overnight charges.
- `mta_tax`: 0.50 dollar MTA tax that is automatically triggered based on the metered rate in use.
- `tip_amount`: Tip amount. This field is automatically populated for credit card tips. Cash tips are not included.
- `tolls_amount`: Total amount of all tolls paid in trip.
- `imp_surcharge`: 0.30 dollar improvement surcharge assessed on hailed trips at the flag drop. The improvement surcharge began being levied in 2015.
- `airport_fee`: -
- `total_amount`: The total amount charged to passengers. Does not include cash tips.
- `pickup_location_id`: TLC Taxi Zone in which the taximeter was engaged.
- `dropoff_location_id`: TLC Taxi Zone in which the taximeter was disengaged.
- `data_file_year`: Datafile timestamp year value.
- `data_file_month`: Datafile timestamp month value.

It is important to note that the dataset only includes data for yellow taxis in New York City, and does not include data for other types of taxis or for other cities.
