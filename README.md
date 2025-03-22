# Yelp Business Reviews Sentimental and Data Analysis

## Tools Used
### Jupyter notebook, Amazon S3, Snowflake

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
### 6. Repeated the same step for `yelp_businesses` table.
### 7. To perform sentiment analysis on the reviews, used Python library `TextBlob` for sentiment analysis classifying the reviews as Positive, Negative, or Neutral.
![image](https://github.com/user-attachments/assets/ea301a4e-b984-4ea8-a608-c85532691c72)




