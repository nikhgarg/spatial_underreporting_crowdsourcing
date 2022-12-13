# Public repository for quatifying under-reporting 

## Data preparation

To get the data needed, use [this link](https://www.dropbox.com/sh/s2y580sm0vtqt27/AAChljhueTtRGou_rxVbHw6Aa?dl=0) and download the two zip files. 

Extract `nyc_data.zip` into `nyc/data/`, and extract `chicago_data.zip` into `chicago/data/`.

### Data description

#### `nyc_data.zip`

- `FSR_221022`: public accessible 311 service requests made to the Forestry unit of NYC Parks. This dataset is actively maintained, and this version was retrieved 10/22/2022 at 14:45 EDT from [NYC Open Data](https://data.cityofnewyork.us/Environment/Forestry-Service-Requests/mu46-p9is)
- `FI_221022`: public accessible data on inspections conducted by the Forestry unit of NYC Parks. This dataset is actively maintained, and this version was retrieved 10/22/2022 at 14:32 EDT from [NYC Open Data](https://data.cityofnewyork.us/Environment/Forestry-Inspections/4pt5-3vv4)
- `FWO_221022`: public accessible data on work orders completed by the Forestry unit of NYC Parks. This dataset is actively maintained, and this version was retrieved 10/22/2022 at 14:31 EDT from [NYC Open Data](https://data.cityofnewyork.us/Environment/Forestry-Work-Orders/bdjm-n7q4)
- `FRA_221024`: public accessible data on risk assessments by the Forestry unit of NYC Parks. This dataset is actively maintained, and this version was retrieved 10/24/2022 at 14:30 EDT from [NYC Open Data](https://data.cityofnewyork.us/Environment/Forestry-Risk-Assessments/259a-b6s7)

#### `chicago_data.zip`

- `311_Service_Requests.csv`: publicly accesible 311 service requests data from City of Chicago. This dataset is actively maintained, and this version was retrieved 7/4/2022 at 21:20 EDT from [Chicago Data Portal](https://data.cityofchicago.org/Service-Requests/311-Service-Requests/v6vf-nfxy)
- `SR_to_census_tracts_full.csv`: a dataframe listing census tract of each service request, generated by passing the lat-long coordinates of each service request through the FCC API
- `tract_adjacency.npz` and `tract_order_adjacency`: contains the adjacency information of census tracts, used to generate spatial priors in ICAR model
- `shapefiles/` contains the shapefiles and related database files of census tracts in the state of Illinois as of 2017, retrieved from [data.gov](https://catalog.data.gov/dataset/tiger-line-shapefile-2017-state-illinois-current-place-state-based)

#### Other data used

- `nyc/data/census_organized_all.csv`, `chicago/data/census_organized_all.csv`: census tract demographic information, raw data of which were retrieved from the US Census Bureau
- `nyc/visualize/viz_data/*.*`: shapefiles used to generate spatial priors and spatial plots in NYC

## Running the models ##

###### Installing all required packages:

``conda create --name <env> --file requirements.txt``

``conda activate <env>``

###### Run models:

After all data are put into place, for NYC, navigate to the root directory and run

```python
python nyc/run_model_public_[modelname].py 
```

For Chicago, run

```python
python chicago/run_model_chicago_[modelname].py
```

where `modelname` corresponds to one of `basic, spatial, demographic, temporal`.

For a demonstration of the run results, refer to `nyc/demo_run_nyc_model.ipynb` and `chicago/demo_run_chicago_model.ipynb`.







