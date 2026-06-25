# Oklahoma Non-Emergency Medical Transport (NEMT) Ride Analysis
*by Angie "Gigi" Campuzano — first independent project, Digital Workshop Center data analytics bootcamp*

## Repository Contents

```
├── Oklahoma_NEMT_Ride_Analysis.ipynb   # Main analysis notebook
├── oklahoma_rides_map.html             # Interactive choropleth map
├── FullDataWithDrivetimeJanFeb2025.csv # Ride request data
├── OkrcRegionLookup.csv                # Region lookup table
├── driver.csv                          # Driver data (for future analysis)
└── README.md
```
## Project Overview

This project analysis of 20,831 real non-emergency medical transport service ride requests that help patients get to medical appointments such as dialysis, physical therapy, routine checkups across Oklahoma (Jan–Feb 2025). I examined the *when*, *what time*, and *where* demand is highest to uncover demand patterns that could help a transport service plan staffing, scheduling, and driver allocation.

**Research Questions:**
1. Which day of the week has the most ride requests?
2. What time of day sees peak demand?
3. Which Oklahoma regions generate the most requests?

## Key Findings

- **Thursday** is the busiest day for ride requests; weekend volume drops sharply, with Sunday the slowest day overall.
- **Noon** is the peak hour for requests, with a secondary morning peak around 7–8 AM — consistent with typical medical appointment scheduling.
- **OKC Metro and Tulsa Metro** together account for roughly two-thirds of all ride requests, while rural regions like Northwest Oklahoma see very little demand.
- A small share of rides (~2%) had an undefined region, likely due to zip codes not present in the lookup table — noted as a data quality limitation.

## Data

| File | Description |
|---|---|
| `FullDataWithDrivetimeJanFeb2025.csv` | Ride request records — pickup/dropoff addresses, timestamps, GPS coordinates, drive times |
| `OkrcRegionLookup.csv` | Zip-code-level lookup mapping Oklahoma zip codes to OKRC regions, counties, and population |
| `driver.csv` | Driver records (start location, work hours/days) — included for future analysis |

> Data was provided by my mentor, Keeko, as part of a hands-on data analytics project using real-world transportation data.

## Methods & Tools

- **Python** — pandas, matplotlib, geopandas, folium
- **Data cleaning** — handled missing values, converted text dates to datetime
- **Feature engineering** — extracted zip codes from raw address strings using string parsing; derived weekday and hour from timestamps
- **Data merging** — joined ride data to a region lookup table on zip code (SQL-style left join)
- **Visualization** — four matplotlib charts (rides by weekday, hour, and region — bar and pie) with highlighted insight titles
- **Geospatial mapping** — built an interactive choropleth map of Oklahoma counties using county shapefiles from the U.S. Census Bureau, merged with ride counts via Folium

## Visualizations

This project includes:
- Bar chart — total rides by weekday (Thursday highlighted)
- Bar chart — total rides by hour, 5 AM–9 PM (noon highlighted)
- Bar chart and pie chart — rides by Oklahoma region
- **Interactive choropleth map** (`oklahoma_rides_map.html`) — open in any browser to zoom/pan across Oklahoma counties, colored by total ride volume
