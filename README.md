# Yelp Business Reviews Sentimental and Data Analysis

## Tools Used
### Jupyter notebook, Amazon S3, Snowflake

## Table of Contents
1. [Dataset description](#dataset-description)
2. [Project Workflow](#project-workflow)
3. [Data Analysis in Snowflake](#data-analysis-in-snowflake)
4. [Future Work](#future-work)

## Dataset description
### Download Yelp open dataset in JSON format: https://business.yelp.com/data/resources/open-dataset/
### This dataset contains 1 compressed TAR file (4.35 GB). Uncompressed it contains 1 PDF and 5 JSON files (8.65 GB). Documentation is included.
### 1. business.json
#### Contains business data including location data, attributes, and categories. 
![image](https://github.com/user-attachments/assets/a773b883-e072-4ec4-8098-d5802b8e7c92)
![image](https://github.com/user-attachments/assets/ae89affa-a08d-4986-b76e-359704b4b20e)
### 2. review.json
#### Contains full review text data including the user_id that wrote the review and the business_id the review is written for. 
![image](https://github.com/user-attachments/assets/4cc8f5b6-ff63-4bca-b606-4c0a853c5e22)
![image](https://github.com/user-attachments/assets/802000f6-c4b3-4f97-954a-a369cf1ab5b4)
### 3. user.json
#### User data including the user's friend mapping and all the metadata associated with the user. 
### 4. checkin.json
#### Checkins on a business. 
### 5. tip.json
#### Tips written by a user on a business. Tips are shorter than reviews and tend to convey quick suggestions. 

## Project Workflow
![image](https://github.com/user-attachments/assets/cda13fc8-dcdf-4389-b774-4856d055d795)
### 1. Downloaded the Yelp open dataset.
### 2. As the file is very large (5 GB), it is not feasible to directly work on this dataset.
### 3. So created a Python script `splitting_files.ipynb` which splits the whole dataset into 10 smaller datasets.
#### Note: You can review the file in `splitting_code` folder above.
### 4. After splitting, the json files are uploaded in Amazon S3 bucket along with yelp_academic_dataset_business.json .
### 5. In Snowflake, created a new table `yelp_reviews` by copying the data from Amazon S3 bucket using AWS_KEY_ID and AWS_SECRET_KEY.
![image](https://github.com/user-attachments/assets/e86e3ab0-6d05-42a9-b300-875594b2795d)
### 6. Repeated the same step for `yelp_businesses` table.
![image](https://github.com/user-attachments/assets/6b798025-43ff-48f2-a584-a9b942ae623a)
### 7. To perform sentiment analysis on the reviews, used Python library `TextBlob` for sentiment analysis classifying the reviews as Positive, Negative, or Neutral.
![image](https://github.com/user-attachments/assets/ea301a4e-b984-4ea8-a608-c85532691c72)
### 8. As the data is in comma separated format, we need to convert it into tabular format for performing data analysis in Snowflake.
### 9. Created a new table `tbl_yelp_reviews` having only the necessary columns.
![image](https://github.com/user-attachments/assets/9ba84bf6-df47-45c7-8888-be64b5f36cae)
### 10. Created another table `tbl_yelp_businesses` having only the necessary columns.
![image](https://github.com/user-attachments/assets/f9c95916-c8cb-4b81-be2e-85cd294551de)
### Now our data is created and well maintained to be used for further analysis.

## Data Analysis in Snowflake

### 1. Find the number of businesses in each category.
![image](https://github.com/user-attachments/assets/c14cda94-3fcf-425e-ba6b-097068b74566)
### 2. Find the top 10 users who have reviewed the most businesses in the 'Restaurants' category.
![image](https://github.com/user-attachments/assets/b02b5418-60f9-4e09-b6f9-3ba9f492d96d)
### 3. Find the most popular categories of businesses based on number of reviews.
![image](https://github.com/user-attachments/assets/61368b66-6fba-4e14-b530-2832d4e6ab0c)
### 4. Find the top 3 most recent reviews for each business.
![image](https://github.com/user-attachments/assets/3c7d8d3e-2e05-4920-8550-53e97fa59095)
### 5. Find the month having highest number of reviews.
![image](https://github.com/user-attachments/assets/98bb8612-2fbd-4d4e-8453-b69c03dd85af)
### 6. Find the percentage of 5-star reviews for each business.
![image](https://github.com/user-attachments/assets/ccc9111b-6cbc-43ec-96ba-017fabb213ac)
### 7. Find the top 5 most reviewed businesses in each city.
![image](https://github.com/user-attachments/assets/4d814c4e-be2a-4b23-b8bc-e71911bd6bcf)
### 8. Find the average rating of businesses that have atleast 100 reviews.
![image](https://github.com/user-attachments/assets/1176351f-07e0-4156-8206-171dec7de4b5)
### 9. List the top 10 users who have written the most reviews, along with the businesses they reviewed.
![image](https://github.com/user-attachments/assets/7178297a-cdf6-4fb6-b8d0-55720fe05bd8)
### 10. Find the top 10 businesses with highest positive sentiment reviews.
![image](https://github.com/user-attachments/assets/f84e50ce-d62b-4cf3-a9ec-f56b76671985)

## Future Work
### As the data analysis is done in Snowflake only, we can extend our analysis more visually using Power BI dashboard.











