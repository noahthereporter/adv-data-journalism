# Analysis of New York and Boston Government Backed EV Charging Infrasturcture — 10/2024

This repository contains data, analytic code, and findings that support portions of the article, “[Maybe New York isn't so behind on EV charging after all](https://www.google.com),” published 10/18/2024. Please read that article, which contains important context and details, before proceeding.

## Data

This analysis uses four spreadsheets.

The spreadsheets come from the following sources:

- Name of source: [New York State OpenData](https://data.ny.gov/Transportation/Vehicle-Snowmobile-and-Boat-Registrations/w4pv-hbkt/about_data)
  - `NY Vehicle registrations.csv`: Raw data of vehicle registrations in the state.

- Name of source: [New York City OpenData](https://data.cityofnewyork.us/City-Government/NYC-EV-Fleet-Station-Network/fc53-9hrv/about_data)
  - `NYC EV chargers.csv`: Raw data of EV chargers in New York City.

- Name of source: [Mass Gov Data](https://geodot-massdot.hub.arcgis.com/datasets/27460234daed45e3b37555d77d7bc861/about)
  - `Boston_Bi_Annual.csv`: Raw data of the Massachusetts Bi-annual Motor Vehicle Census.

- Name of source: [Boston OpenData](https://bostonopendata-boston.opendata.arcgis.com/datasets/465e00f9632145a1ad645a27d27069b4/explore)
  - `Boston Electric_Vehicle_Charging_Stations.csv`: Raw data of chargers in the Boston area.

## Methodology

The notebook [`NYC_vs_Boston_EV_Infrastructure.ipynb`](notebooks/NYC_vs_Boston_EV_Infrastructure.ipynb) performs the following analyses:

##### Part 1: Filtering

- After compiling the notebook and importing the data, I needed to filter each dataset down to the geographical and EV focused needs of the project.
  -New York State Registration Data: This was filtered by Record Type to specify it was an automobile, Registration Class to narrow it down to passenger vehicles, County to narrow it down to specifically vehicles used in New York City and Fuel Type to narrow down to electric vehicles.
  -New York City Charger Data: This was just filtered by station type to narrow down to the DOT Flo zcurbside charging units.
  -Boston Motor Vehicle Census: I first had to filter this by date to get to the most recent census data taken on the first of July, then I had to filter by Municipality so I could narrow to Boston, I also had to filter VehicleUse to Passenger to narrow to the proper vehicle type and finally, I had to filter by AdvancedVehicleType to narrow that down to electric.
  -Boston Charger Data: For this dataset I had to filter with two conditions. First, I had to narrow the owner_type_code to the governments, then I had to narrow the city to Boston.


##### Part 2: Comparing

-I then did a simple compairson by summing the number of plugs for each city and the number of reported EVs for the area and divided them out to get get the number of cars per charger for each city.


## Outputs

The notebooks output these four spreadsheets, which contains the filtered verisons of each of the inputted datasets.: [`output/NYC_EVs.csv`](output/NYC_EVs.csv), [`output/NYC_Public_Chargers.csv`](output/NYC_Public_Chargers.csv), [`output/Boston_EV_Count.csv`](output/Boston_EV_Count.csv), [`output/Boston_Public_Chargers.csv`](output/Boston_Public_Chargers.csv).

## Running the analysis yourself

You can run the analysis yourself. To do so, you'll need the following installed on your computer:

- Python 3
- The Python libraries specified in [`requirements.txt`](requirements.txt)

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). The data file in the output/ directory is available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions?

Contact Noah at your.name@email.com.
