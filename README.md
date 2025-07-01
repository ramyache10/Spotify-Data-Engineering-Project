# Spotify End to End Data-Engineering-Project
### Introduction
This project demonstrates a complete data engineering workflow using AWS services. It extracts Spotify playlist data via API, processes it with AWS Lambda, transforms it into structured formats (albums, songs, artists), stores the outputs in S3, and enables querying via AWS Athena and Glue Data Catalog.

## #🗺️ Architecture
![Architecture Diagram](https://github.com/ramyache10/Spotify-Data-Engineering-Project/blob/main/Architecture_diagram.png)

### 🧰 AWS Services Used

| Service        | Purpose                                                                 |
|----------------|-------------------------------------------------------------------------|
| **AWS Lambda** | Serverless compute to extract and transform Spotify data                |
| **Amazon S3**  | Store raw and transformed data                                          |
| **AWS Glue**   | Create crawler to infer schema and build data catalog                   |
| **AWS Athena** | Query transformed data using SQL                                        |
| **CloudWatch** | Schedule Lambda function execution with EventBridge/cron jobs          |
| **IAM**        | Grant least-privilege access to services and Lambda execution role      |

                            
### 🔁 ETL Process

- **Extract**: Lambda fetches playlist data from the Spotify API (songs, artists, albums)
- **Transform**: Data is parsed and formatted into structured CSV using Pandas
- **Load**: Transformed data is saved to Amazon S3 in structured folders
- **Catalog**: AWS Glue crawlers catalog the data into tables
- **Query**: Athena queries the tables using SQL-like syntax

  ## ▶️ How to Run

1. Set up IAM roles with access to S3, Lambda, Glue, and Athena
2. Deploy the Lambda function and upload your script (etl_lambda.py)
3. Use CloudWatch EventBridge rule to schedule data extraction
4. Run Glue crawler to create table schema
5. Use Athena to write queries like:
```sql
SELECT song_name, popularity FROM songs_data WHERE popularity > 80;
```
