# Machine-Learning-1
Movie Recommendation with MLlib - Collaborative Filtering

![Movie Recommendation System Google Slides](https://docs.google.com/presentation/d/15jcTUw9K7MhRJLJDpDry72jAdmj-Bm6eZAkxKPCii6A/edit#slide=id.g27efc1821a1_0_47)

# Movie Recommendation with MLlib - Collaborative Filtering


## Introduction

This project showcases the implementation of a movie recommendation system using PySpark's MLlib Collaborative Filtering algorithm. Collaborative Filtering is a powerful technique for creating personalized recommendation systems by predicting user preferences based on patterns and similarities observed among users and items.

## Design

![Movie Recommendation System Flowchart]
![flowchart](https://github.com/franketang/Machine-Learning-1/assets/29631514/fdd58178-e067-411f-8196-da4686e5709f)

The movie recommendation system is built using the Collaborative Filtering approach, which involves the following key steps:

1. **Loading and Parsing the Input Data**: We start by loading and parsing the input data, which comes from the MovieLens dataset containing user ratings. This data is transformed into the Resilient Distributed Dataset (RDD) format required for our analysis.

2. **Building the Recommendation Model**: To create recommendations, we employ the ALS (Alternating Least Squares) algorithm. ALS is an iterative optimization algorithm that factorizes the user-item matrix into two lower-rank matrices representing user and item features. The "rank" parameter determines the number of features used in this factorization.

3. **Evaluating the Model**: The performance of our recommendation model is assessed using the Mean Squared Error (MSE) metric. MSE measures the average squared difference between the predicted and actual ratings. A lower MSE signifies a better-performing model.

4. **Saving the Model**: Once trained, the recommendation model can be saved to a specified location for future use and deployment.

## Implementation

### Prerequisites

Before you can implement this movie recommendation system, ensure you have the following prerequisites in place:

1. **Google Cloud Platform Account**: Sign up for a Google Cloud Platform (GCP) account if you don't have one already.

2. **Google Cloud Storage Bucket**: Create a GCS bucket to store the input data.

3. **Dataproc Cluster**: Set up a Dataproc cluster with the necessary configuration and access to the GCS bucket.

### Steps

The implementation consists of the following steps:

1. **Download the MovieLens Data**: Fetch the `movielens.txt` file from your GCS bucket using `gsutil`:

   ```
   gsutil cp gs://cs570-bigdata-pyspark/movielens.txt .
   ```

2. **Convert the Data Format**: Use the following command to convert the `movielens.txt` data into the desired format:

   ```bash
   cat movielens.txt | while read userid movieid rating timestamp; do echo "${userid},${movieid},${rating}"; done > converted_data.txt
   ```

3. **Verify the Data**: Check the contents of the converted data by running:

   ```
   cat converted_data.txt
   ```

4. **Upload the Data**: Upload the `converted_data.txt` file to your GCS bucket:

   ```
   gsutil cp converted_data.txt gs://your-bucket-name/recommendation/
   ```

5. **Create a Dataproc Cluster**: Set up a Dataproc cluster on GCP with the necessary configurations and ensure it has access to the GCS bucket.

6. **Submit the Job**: Using the GCP Console, submit a job for processing. Specify the job details, including the cluster, job type (PySpark), and the main Python file location (e.g., `gs://your-bucket-name/recommendation/recommendation.py`).

7. **Check the Output**: Monitor the job progress and check the output for your movie recommendations.

By following these steps, you can successfully implement and run the movie recommendation system using MLlib Collaborative Filtering on Google Cloud Platform. This system leverages the power of PySpark and GCP to provide personalized movie recommendations based on user preferences.
