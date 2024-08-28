# Tekken Subreddit ETL Pipeline

Hello! This project demonstrates the process of extracting data from the Tekken subreddit, transforming it, and visualizing the results. The data is collected using the PRAW library, stored in AWS S3, processed using AWS Glue, and visualized using Looker Studio.

![image](https://github.com/user-attachments/assets/feb8f4b4-491c-45f0-9b15-8efe13ed65c4)



## Project Workflow

- **Data Extraction**:
       -- Used PRAW (Python Reddit API Wrapper) to extract data from the Tekken subreddit.
        Extracted fields include Title, Score, Upvote_Ratio, Number_of_Comments, Url, Author, Flair, and Created_UTC.
-- The extracted data was converted as a CSV file.
- **Data Storage**:
-- Uploaded the CSV file to an S3 bucket on AWS for storage.
- **Data Cataloging**:
--  Created a Glue Crawler to automatically catalog the CSV file stored in S3.
-- The Glue Crawler generated a table in the AWS Glue database based on the CSV data.
- **Data Transformation (ETL)**:
        - Used AWS Glue's visual editor to perform the following ETL operations:
           - Remove Nulls: Identified and removed columns containing only null values.
           - Timestamp Transformation: Converted the UNIX timestamp (Created_UTC) to a human-readable date format.
            - SQL Query: Executed a SQL query to sort the data by the Year column.
        - The transformed data was then written back to an S3 bucket as a CSV file.

- **Data Visualization**:

	-- Uploaded the final processed CSV file to Looker Studio.
	-- Created three charts to visualize the data:
            -- Trend of Score: Analyzed the trend of scores over time.
            -- Metadata: Provided an overview of key metadata from the posts.
            -- Most Scored by Flair: Visualized which flairs received the highest scores.

    The Looker Studio dashboard can be accessed here:
    https://lookerstudio.google.com/reporting/c58f420a-e8e4-4bc8-b876-e6b487e9210d/page/qrBAE
