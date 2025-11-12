# DataBricks_Hackathon
A repo to track Databricks DataEngineering project

Necessary to install Databricks on the github repo
## Dataset
We are using this datset from Kamen Lab Bioprocessing Repository (McGill University).
Multivariate data analysis on multi-sensor measurement for in-line process monitoring of adenovirus production in HEK293 cells
https://borealisdata.ca/dataset.xhtml?persistentId=doi:10.5683%2FSP3%2FKJXYVL
Project Desciption: Digital-twin of bioreactor for accelerated design and optimal operations in production of complex biologics - Mechanistic models to describe biological processes more realistically. Four multi-sensor bioprocess time series datasets to support the manuscript titled: "Multivariate data analysis on multi-sensor measurement for in-line process monitoring of adenovirus production in HEK293 cells." Under review at Biotechnology and Bioengineering. (2024-01-23)

## Using Guidance
https://customer-academy.databricks.com/learn/courses/2469/get-started-with-databricks-for-data-engineering

### Lakeflow
1. upload files to a volume (selta lake)
2. create a table form files
3. Lakeflow declarative pipeline
Bronze -> clean -> Silver -> Filter/Enrich -> Silver -> Agreggate -> Gold
* triggers to feed data to databricks lakeflow
* control flow to assess data quality
* observability to assess data drift

### DeltaLake -> ACID transactions
1. connect to a cloud provider (AWS, Azure, GCP)
2. Define DeltaTableName
* using data_log to track 