# DataBricks_Hackathon
A repo to track Databricks DataEngineering project

Necessary to install Databricks on the github repo
## Dataset
We are using this datset from Kamen Lab Bioprocessing Repository (McGill University).
Multivariate data analysis on multi-sensor measurement for in-line process monitoring of adenovirus production in HEK293 cells
https://borealisdata.ca/dataset.xhtml?persistentId=doi:10.5683%2FSP3%2FKJXYVL
Project Desciption: Digital-twin of bioreactor for accelerated design and optimal operations in production of complex biologics - Mechanistic models to describe biological processes more realistically. Four multi-sensor bioprocess time series datasets to support the manuscript titled: "Multivariate data analysis on multi-sensor measurement for in-line process monitoring of adenovirus production in HEK293 cells." Under review at Biotechnology and Bioengineering. (2024-01-23)


### LIST OF FILES

  Four bioreactors were operated in batch or fed-batch modes (refer to Table 1
  in publication for more details):

    1) Adenovirus 1 (AdV01)
    2) Adenovirus 2 (AdV02)
    3) Adenovirus 3 (AdV03)
  
 
  ### Explanation:
    * An Excel spreadsheet of bioprocess data, each containing three sheets,
      named like '*_LucullusBioprocessData.xlsx'. Sheet contents:

        - Sheet 1, 'Lucullus Data':
            Bioprocess data exported from Lucullus, including dielectric data
        - Sheet 2, 'Capacitance':
            Dielectric data acquired via Futura SCADA
        - Sheet 3, 'Explain' (excluding batch CG):
            Lucullus variable (port) specifications

    * An '*_MWF/spectra/' directory. This contains the emission spectra data
      produced by the multi-wavelength fluorometer. WE DON'T USE THIS

  Capacitance ---> in situ measurment (sampling rate = 1 minute)
  Lucullus Data -> ex situ measurment (sampling rate = 5 minute)

  ```
  $ \tree -nF

  ./
  ├── README.txt
  ├── mvda_adenovirus_bioprocess_data.tar.gz.sha256
  ├── mvda_adenovirus_bioprocess_data.tar.gz/      # (contents after extracting)
  │   ├── AdV01_LucullusBioprocessData.xlsx
  │   ├── AdV01_MWF/
  │   │   ├── AdV01.time
  │   │   ├── Spec_Area1.txt
  │   │   ├── changes.txt
  │   │   ├── predict_var.txt
  │   │   └── spectra/
  │   │       ├── AdV01_00000.dat
  │   │       ├── ...
  │   │       └── AdV01_01733.dat
  │   ├── AdV02_LucullusBioprocessData.xlsx
  │   ├── AdV02_MWF/
  │   │   ├── AdV02.time
  │   │   ├── Spec_Area1.txt
  │   │   ├── background.txt
  │   │   ├── changes.txt
  │   │   ├── predict_var.txt
  │   │   └── spectra/
  │   │       ├── AdV02_00000.dat
  │   │       ├── ...
  │   │       └── AdV02_01732.dat
  │   ├── AdV03_LucullusBioprocessData.xlsx
  │   ├── AdV03_MWF/
  │   │   ├── AdV03.time
  │   │   ├── Spec_Area1.txt
  │   │   ├── background-OFF.txt
  │   │   ├── background-oN.txt
  │   │   ├── changes.txt
  │   │   ├── predict_var.txt
  │   │   └── spectra/
  │   │       ├── AdV03_00000.dat
  │   │       ├── ...
  │   │       └── AdV03_01226.dat
  │   ├── CellGrowth_LucullusBioprocessData.xlsx
  │   └── CellGrowth_MWF/
  │       ├── CellGrowth.time
  │       ├── Spec_Area1.txt
  │       ├── predict_var.txt
  │       └── spectra/
  │           ├── CellGrowth_00000.dat
  │           ├── ...
  │           └── CellGrowth_02013.dat
  ├── ExampleData.xlsx
  └── ProcessedVariables.xlsx
  
  10 directories, 6734 files
  (count includes README.txt and *.sha256 files at top-level)
  ```



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