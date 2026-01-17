# Crypto Exchange Data Pipeline

This project implements a data pipeline using **Airflow** and **Google Cloud** to extract, transform, and load cryptocurrency data from the CoinGecko API.

## Overview

The pipeline performs the following steps:

1. **Fetch data** from the CoinGecko API.  
2. **Store raw data** in Google Cloud Storage bucket (GCS).  
3. **Transform the data** locally into a clean CSV format with timestamps.  
4. **Upload transformed data** to GCS bucket.  
5. **Load the data** into BigQuery for analysis.  
6. Visualize the data using Looker.
   
<img width="1790" height="836" alt="_Diagrama de flujo" src="https://github.com/user-attachments/assets/5b8be599-1d6b-4ac4-84f0-a29f491aaf94" />

There are two DAGs included:

- **Local Airflow DAG**: Runs on a local Airflow setup.  
- **Google Composer DAG**: Runs on Google Cloud Composer.

Both DAGs follow the same ETL process but are configured for their respective environments.

## DAG Structure

- **fetch_data_from_api** — Fetches cryptocurrency data from CoinGecko.  
- **create_bucket** — Creates a GCS bucket if it doesn’t exist.  
- **upload_raw_data_to_gcs** — Uploads raw JSON data to GCS.  
- **transform_data** — Processes raw data into CSV format.  
- **upload_transformed_data_to_gcs** — Uploads transformed CSV to GCS.  
- **create_bigquery_dataset** — Creates BigQuery dataset if needed.  
- **load_to_bigquery** — Loads CSV data from GCS into BigQuery.


## Development and Test Evidence

Below are images documenting key steps during development and testing:

1. **Service Account Creation**

<img width="944" height="395" alt="Create Service account" src="https://github.com/user-attachments/assets/f0b91fd4-c59a-4619-9e31-b6292cc41627" />

*Creating the service account in Google Cloud.*

2. **Assigning Permissions**

<img width="684" height="445" alt="Grant service account access" src="https://github.com/user-attachments/assets/a05d66bb-d7e6-4d6f-acb4-073def8fe3c0" />

*Granting roles: Owner, Composer Admin, Composer API Service Agent, Composer API Extension.*

3. **Saving Composer Key Locally**

<img width="953" height="325" alt="Create private key" src="https://github.com/user-attachments/assets/138bc927-a3c3-4d7a-963f-ddb834a1b0d5" />

*Storing the private key in the specified local path.*

4. **Enabling Cloud Composer API**

<img width="533" height="319" alt="Enable Cloud Composer API" src="https://github.com/user-attachments/assets/ccd98b01-4949-451c-89e1-6c0c94fa0fca" />

*Activating the Cloud Composer API for the project.*

5. **Creating Composer Environment**

<img width="692" height="277" alt="Create environment" src="https://github.com/user-attachments/assets/cba68645-92fe-40ce-8604-191a93080dbd" />

*Setting up a new Composer environment.*

<img width="691" height="420" alt="Create environment configuration" src="https://github.com/user-attachments/assets/cddf4a3e-e18f-49a4-ab6d-ee7127bae913" />

*Create environment configuration.*

6. **Updating Docker-Compose**

<img width="559" height="159" alt="Add Requirements to work with google cloud" src="https://github.com/user-attachments/assets/9d5bcf3c-c990-4167-a656-f867a057c6db" />

*Adding required dependencies for Google Cloud connection.*

7. **Storing Credentials**

<img width="658" height="139" alt="Copy json key into config location" src="https://github.com/user-attachments/assets/717258b3-39da-4e0b-b73e-3e8e33bd2908" />

*Placing credentials in the enabled path for Airflow.*

8. **Creating Airflow Connection**(local)

<img width="446" height="299" alt="Create connection to Google Cloud from airflow" src="https://github.com/user-attachments/assets/6cda0cbc-99c9-4be9-9b21-e40f7ff246a7" />

*Configuring Google Cloud connection in local Airflow.*

9. **Test Data Fetching**

<img width="368" height="385" alt="Create DAG crypto_exchange_pipeline" src="https://github.com/user-attachments/assets/86438aab-88ac-4437-ace5-26849181f096" />

<img width="925" height="302" alt="DAG test" src="https://github.com/user-attachments/assets/8b3ec374-cccb-4741-b655-d44a1f2eae14" />

*Testing data retrieval from the API.*

10. **Test BigQuery Provisioning**

<img width="957" height="470" alt="Store raw data in gc bucket" src="https://github.com/user-attachments/assets/f0024d54-e5f1-4e68-9de6-8ca5e9de2aa9" />

*Checking data load into BigQuery.*

11. **Inspect Raw Data**

<img width="958" height="287" alt="Example data store" src="https://github.com/user-attachments/assets/7cdfd3a8-c15d-43b6-97ec-5d0c22934fed" />

*Viewing the raw data in GCS.*

12. **Running Pipeline on Composer**

<img width="956" height="471" alt="Execute DAG from Google composer" src="https://github.com/user-attachments/assets/17f7ace3-0e13-4358-a377-140d1e682a5a" />

*Executing the pipeline from Cloud Composer.*

13. **Looker Visualization**

<img width="723" height="409" alt="test crypto dashboard" src="https://github.com/user-attachments/assets/1bcba990-ab84-45f2-97b6-9c403ff3d1b9" />
<img width="811" height="216" alt="Resultados" src="https://github.com/user-attachments/assets/070469da-acc4-4e68-b3b8-f20d1e158619" />

*Displaying the processed data in Looker.*

14. **Composer DAG Details**

<img width="923" height="313" alt="Estadísticas del DAG" src="https://github.com/user-attachments/assets/86a2990a-0f23-451d-8961-7d0734ca5dd1" />

*Additional DAG details in Google Composer.*
