**Project Description**: This project automates the creation and deletion of a data lake for NBA analytics using AWS services. The script `setup_nba_data_lake.py` integrates Amazon S3, AWS Glue, and Amazon Athena, and set up the infrastructure needed to store and query NBA-related data.

The `nba_datalake.py` script performs the following actions:
```
Creates an Amazon S3 bucket to store raw and processed data.
Uploads NBA data (JSON format) to the S3 bucket.
Creates an AWS Glue database and an external table for querying the data.
Configures Amazon Athena for querying data stored in the S3 bucket.
```
The `delete_resources.py` script performs the following actions:
```
Deletes the Amazon S3 bucket and its contents.
Deletes the AWS Glue database and associated tables.
Deletes Athena query results stored in the S3 bucket.
```
**Prerequisites**

Before running the scripts, ensure you have the following:
```
SportsData.io Account:
Sign up for a free account at SportsData.io.
Obtain your NBA API key from the "Standings" section.

IAM Permissions:
S3: s3:CreateBucket, s3:PutObject, s3:DeleteBucket, s3:ListBucket
Glue: glue:CreateDatabase, glue:CreateTable, glue:DeleteDatabase, glue:DeleteTable
Athena: athena:StartQueryExecution, athena:GetQueryResults
```

**Directory Structure**:
```
├── policies/                # contains the IAM policy required for the scripts to execute successfully
├── src/                     # Source code directory
│   ├── nba_datalake.py      # Main application logic
│   └── .gitignore           # Git ignored files
│   └── .env                 # Environment variables file
├── delete_resources.py      # Delete resources created
├── requirements.txt         # Python dependencies
└── README.md                # Project documentation
```
**Setup Instructions**:
```
Clone the repository:
git clone https://github.com/charity-web/NBA-Datalake.git
cd NBADataLake

Install the required Python packages:
pip install -r requirements.txt

Create a .env file in the src directory with the following content:
cd src
touch .env
SPORTS_DATA_API_KEY=<your_sportsdata_api_key>
NBA_ENDPOINT=https://api.sportsdata.io/v3/nba/scores/json/Players
```
**Usage**:

Setting Up the Data Lake

Run the nba_datalake.py script to set up the data lake:
```sh
python src/nba_datalake.py
```

The above script will:
```
Create an S3 Bucket: An S3 bucket will be created to store raw and processed NBA data.
Create a Glue Database: An AWS Glue database will be created to catalog the data.
Fetch NBA Data: NBA data will be fetched from the Sportsdata.io API.
Upload Data to S3: The fetched data will be uploaded to the S3 bucket.
Create a Glue Table: An external table will be created in AWS Glue to query the data.
Configure Athena: Amazon Athena will be configured to query the data stored in the S3 bucket.
Querying Data with Athena
```

After setting up the data lake, you can query the data using Amazon Athena. Here are the steps:
```
Go to the Amazon Athena console.
Select the database created by the script.
Write and execute SQL queries to analyze the NBA data.
Deleting the Data Lake Resources
```
Run the `delete_resources.py` script to delete the data lake resources:

```sh
cd ..
python delete_resources.py
```
The above script will:
```
Delete the S3 Bucket: The S3 bucket and its contents will be deleted.
Delete the Glue Database: The AWS Glue database and associated tables will be deleted.
Delete Athena Query Results: Any Athena query results stored in the S3 bucket will be deleted.
```

