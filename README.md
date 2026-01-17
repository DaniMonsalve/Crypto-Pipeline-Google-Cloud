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


*Creating the service account in Google Cloud.*

2. **Assigning Permissions**


*Granting roles: Owner, Composer Admin, Composer API Service Agent, Composer API Extension.*

3. **Saving Composer Key Locally**


*Storing the private key in the specified local path.*

4. **Enabling Cloud Composer API**


*Activating the Cloud Composer API for the project.*

5. **Creating Composer Environment**


*Setting up a new Composer environment.*

6. **Updating Docker-Compose**


*Adding required dependencies for Google Cloud connection.*

7. **Storing Credentials**


*Placing credentials in the enabled path for Airflow.*

8. **Creating Airflow Connection**


*Configuring Google Cloud connection in local Airflow.*

9. **Test Data Fetching**


*Testing data retrieval from the API.*

10. **Test BigQuery Provisioning**


*Checking data load into BigQuery.*

11. **Inspect Raw Data**


*Viewing the raw data in GCS.*

12. **Running Pipeline on Composer**


*Executing the pipeline from Cloud Composer.*

13. **Looker Visualization**


*Displaying the processed data in Looker.*

14. **Composer DAG Details**


*Additional DAG details in Google Composer.*