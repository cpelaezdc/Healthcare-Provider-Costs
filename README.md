# Healthcare-Provider-Costs

## Introduction

In this project, we'll develop an ETL pipeline using Apache NiFi to process healthcare data from Medicare.gov's procedure price lookup. This rich dataset allows us to analyze pricing trends across various medical specialties and zip codes throughout the United States. By extracting the data, we can identify minimum, maximum, and most frequent (mode) prices charged by Medicare-certified suppliers, providing valuable insights into healthcare cost variations.

### Key Components:

*  Data Extraction: Utilizing NiFi to extract data from Medicare.gov APIs.
*  Data Transformation: Processing and preparing the data for analysis.
*  Data Loading: Loading the processed data into a data warehouse.
*  Data Visualization: Leveraging Power BI to create interactive dashboards and visualizations for insightful analysis.


## Arquitecture
![Arquitecture](assets/Arquitecture.png)


## Tools:
*  Programming Language - NiFi Expression Language
*  Scripting Language - SQL
*  Pipeline software - NIFI
*  Data warehouse - PostgreSQL database
*  Environments - Docker
*  Tests - Postman (Test APIs)
*  Visualisation - PowerBI


## Data Model
![DataModel](/assets/data_model.png)

## Environments
*  NIFI [docker-compose.yml](docker-compose.yml)
*  PosgreSQL [docker-compose.yml](docker-compose.yml) 

## Scripts


## Visualisations


## NIFI Pipeline


## Dataset Used
*  See APIs - [datasets](https://data.cms.gov/provider-data/topics/physician-office-visit-costs)

## Data Sources
-  Official website of the United States government - https://data.cms.gov/provider-data/topics/physician-office-visit-costs


