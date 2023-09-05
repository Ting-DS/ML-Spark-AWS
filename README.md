# Spark ML with AWS EMR - Churn Prediction Model using Sparkify Music App Data

![PySpark]((https://github.com/Ting-DS/Spark_Music_App/blob/main/py_spark.png))


The project insights are in the blog post: [Link]

## Introduction
Sparkify is a music streaming service where users can listen to music, share content, and choose to become paid subscribers. Retaining users is crucial for the company's success, and employing strategies such as offering discounts or implementing other business tactics to potentially churned users can help the company maintain substantial revenue. Therefore, it is imperative to build a machine learning classification model based on user interactions with the platform to **predict churn risk**. Sparkify provides comprehensive user behavior data, totaling **12GB in size**. Analyzing such massive data locally poses a challenge, which is why **Apache Spark** is my preferred analysis tool. Deploying data science pipelines on Spark allows us to leverage distributed systems like **HDFS** to enhance the scalability of our models. **Spark SQL and Spark DataFrame** can be utilized for data cleansing, while **Spark ML** supports algorithms like **Logistic Regression**, **Random Forests**, and other linear expansion models.

In this project, we will utilize relevant services on the AWS platform. We'll begin by loading the entire 12GB dataset (around **27,000,000 records with 18 fields**) from **AWS S3**. Subsequently, we will employ cloud services such as **AWS EMR** and AWS EC2 to deploy ETL and ML pipelines, utilizing Spark for data analysis. This approach will significantly improve data processing efficiency and scalability, enabling us to better predict user churn risk and take corresponding measures to retain them.
