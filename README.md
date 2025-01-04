| APIs | NIFI | POSTGRESQL | DOCKER | POWERBI |
|---|---|---|---|---| 
| Data Source | ETL Pipeline | Data Storage | Containerization | Data Visualization |

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
🚧 **Under Construction** 🚧
![DataModel](/assets/data_model.png)

## Environments

*  NIFI [docker-compose.yml](docker-compose.yml)
*  PosgreSQL [docker-compose.yml](docker-compose.yml) 

Both NIFI and the Data Warehouse in PostgreSQL will be deployed in the same Docker Compose file.  

```yml
version: '3'

services:
  nifi:
    cap_add:
      - NET_ADMIN # low port bindings
    image: apache/nifi:2.0.0
    environment:
      - TZ=America/Montreal
      - NIFI_WEB_HTTP_HOST=nifi
      - SINGLE_USER_CREDENTIALS_USERNAME=dataengineer
      - SINGLE_USER_CREDENTIALS_PASSWORD=dataengineer
      
    container_name: healthcare-nifi
    ports:
      - "8080:8080/tcp" # HTTP interface
      - "8443:8443/tcp" # HTTPS interface
      - "514:514/tcp" # Syslog
      - "514:514/udp" # Syslog
      - "2055:2055/udp" # NetFlow
    volumes:
      - ./drivers:/opt/nifi/nifi-current/drivers
      - ./certs:/opt/certs
      - nifi-conf:/opt/nifi/nifi-current/conf
      
    restart: unless-stopped

  postgres_db:
    image: postgres:latest
    container_name: healthcare-dw
    ports:
      - 5432:5432  
    volumes:
      - ./postgres-datawarehouse:/var/lib/postgresql/data
    environment:
      - POSTGRES_PASSWORD=dataengineer
      - POSTGRES_USER=dataengineer
      - POSTGRES_DB=healthcare 
    
volumes:
  drivers:
  certs:
  nifi-conf:
  postgres-datawarehouse:   
```

Launch the docker compose in same git repository directory:

```bash
docker compose up -d
```

Open NIFI in browser:
```http
https://localhost:8443/
```

As specified in the Docker Compose file, the username and password for both NIFI and Postgres will be identical:
```text
user:  dataengineer
password: dataengineer
```
```text
database name: healthcare
```


## Scripts
🚧 **Under Construction** 🚧


## Visualisations
🚧 **Under Construction** 🚧


## NIFI Pipeline

🚧 **Under Construction** 🚧


## Dataset Used
*  See APIs - [datasets](https://data.cms.gov/provider-data/topics/physician-office-visit-costs)

## Data Sources
-  [Official website of the United States government](https://data.cms.gov/provider-data/topics/physician-office-visit-costs)
- [Stablished Patient Office Visit codes (99211-99215)](https://www.palmettogba.com/palmetto/jmb.nsf/DIDC/AA8LL61250~eServices%20Portal~Electronic%20Comparative%20Billing%20Report%20(eCBR))

