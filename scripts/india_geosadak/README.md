# India Geo Sadak Data

This import contains district wise statistics of facilities such as LgdCode and count of facilities for each district grouped by each facility category. 

## About the dataset
Latest data from GOI Portal has been used for this India Geo Sadak Import. Available in [PMGSY - Open Data](https://geosadak-pmgsy.nic.in/OpenData)

Source: PMGSY National GIS - Open Data PMGSY GeoSadak, Ministry of Rural Development. Dataset description can be found in [this website](https://geosadak-pmgsy.nic.in/)

Note:
The [preprocess](./preprocess.py) script uses a JSON file that has data in the form of facility_id:LgdCode(key-value) which was generated by using the geometry column of the [India Shape File](https://www.kaggle.com/datasets/imdevskp/india-district-wise-shape-files) and geometry column of the [state wise facilities shape file](./data/facilities/). The districts were mapped to their respective lgdcode after using an algorithm that finds if the given point lies under that particular district or not.


## Overview
The dataset consists of facility details of each district along with its geometry(or boundary), each stored as a shapefile inside a zipfile for the respective states. The data can be found in the [data/facilities](./data/facilities) section of the repository.


### Cleaned data
- The output data for can be found in [India_GeoSadak.csv](./India_GeoSadak.csv).

The cleaned csv has the following columns:
 - LgdCode: District Code
 - Facility_Category: Indicates the type of facility
 - Category_Count: Indicates the total count of the facility in that particular district

Some of the rows from each state were removed due to improper mapping of the geosadak facilities to the respective districts.
 - Total number of rows before removal: 783677
 - No of rows removed: 1589
 - Total number of rows after removal: 782088

### TMCF
- [India_GeoSadak.tmcf](./India_GeoSadak.tmcf)

### MCF
- [India_GeoSadak.mcf](./India_GeoSadak.mcf)

### Scripts
- [preprocess.py](./preprocess.py): Cleans up data and generates the cumulative CSV file

## Script usage
Execute the following command from `scripts/` directory to generate the necessary csv, mcf and tmcf files:

```
python -m india_geosadak.preprocess
```
