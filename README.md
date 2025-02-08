# NBADataLake
This repository contains the setup_nba_data_lake.py script, which automates the creation of a data lake for NBA analytics using AWS services. The script integrates Amazon S3, AWS Glue, and Amazon Athena, and sets up the infrastructure needed to store and query NBA-related data.

# Overview
The setup_nba_data_lake.py script performs the following actions:
 - Creates an Amazon S3 bucket to store raw and processed data.
 - Uploads sample NBA data (JSON format) to the S3 bucket.
 - Creates an AWS Glue database and an external table for querying the data.
 - Configures Amazon Athena for querying data stored in the S3 bucket.

# Prerequisites
- AWS Account with the following permissions:
  - S3: CreateBucket, PutObject, DeleteBucket, ListBucket
  - Glue: CreateDatabase, CreateTable, DeleteDatabase, DeleteTable
  - Athena: StartQueryExecution, GetQueryResults
- NBA API key

# Set Up 
1. Clone the Repo
```bash
git clone https://github.com/LilLoveBytes/NBADataLake.git
```
2. Go to the AWS Console, and click the CloudShell icon to open the terminal.
3. Type nano setup_nba_data_lake.py into the shell console and press enter.
4. Copy the code from our repo file: src/setup_data_lake.py to the shell console.
  - Update the api_key variable to your actual key
  - Update the nba_endpoint variable.
  - Update the bucket_name variable.
  - Update the region variable (if necessary).
  - Hit crtl + x to exit, then y to save.
  -  Hit enter to confirm the name.

5. Type python setup_nba_data_lake.py and run the code.
6. Manually check for the resources.
  - Go to S3 and you should see the new bucket with 3 objects inside of it.
  - Click on raw-data and open the file inside of it.

7. Query the data with Athena.
  - Go to Athena and paste the sample query
``` SQL
SELECT FirstName, LastName, Position, Team
FROM nba_players
WHERE Position = 'PG';
```
  - Click run and you should see output under "Query Results"

8. Delete Resources
   - Navigate to the CloudShell console.
   - Type `nano delete_aws_resources`.
   - Copy-and-paste the content from the file src/delete_aws_resources into the console.
   - Update the bucket_name variable to match the bucket created.
   - Hit crtl + x to exit, then y to save.
   - Hit enter to confirm the name
   - Type `python delete_aws_resources` into the console and hit enter.
   - Manually confirm resources have been deleted.


