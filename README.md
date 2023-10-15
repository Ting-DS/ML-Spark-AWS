# Spark ML with AWS EMR
## Build Churn Prediction Model using Sparkify Music App Data

The project insights are wrangled in this [Medium blog post](https://medium.com/@LobsterTing/spark-ml-with-aws-emr-acdfab30ef01)

## Introduction
Sparkify is a music streaming service where users can listen to music, share content, and choose to become paid subscribers. Retaining users is crucial for the company's success, and employing strategies such as offering discounts or implementing other business tactics to potentially churned users can help the company maintain substantial revenue. Therefore, it is imperative to build a machine learning classification model based on user interactions with the platform to **predict churn risk**. Sparkify provides comprehensive user behavior data, totaling **12GB in size**. Analyzing such massive data locally poses a challenge, which is why **Apache Spark** is my preferred analysis tool. Deploying data science pipelines on Spark allows us to leverage distributed systems like **HDFS** to enhance the scalability of our models. **Spark SQL and Spark DataFrame** can be utilized for data cleansing, while **Spark ML** supports algorithms like **Logistic Regression**, **Random Forest**, and other linear expansion models.


<div align="center">
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/py_spark.png" width="80%">
</div>

<div align="center">
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/spark_progress.png" width="100%">
</div>



In this project, we will utilize relevant services on the AWS platform. We'll begin by loading the entire 12GB dataset (around **27,000,000 records with 18 fields**) from **AWS S3**. Subsequently, we will employ cloud services such as **AWS EMR** and AWS EC2 to deploy ETL and ML pipelines, utilizing Spark for data analysis. This approach will significantly improve data processing efficiency and scalability, enabling us to better predict user churn risk and take corresponding measures to retain them.

## Data Source

To access full fataset in AWS S3: "s3n://udacity-dsnd/sparkify/sparkify_event_data.json"

The full dataset contains 26,259,199 records and 18 columns.

Description:
- **Artist**: Composer or artist of the song.
- **Auth**: Login status of the user.
- **firstName**: First name of the user.
- **gender**: Gender of the user.
- **ItemInSession**: Operation sequence number of this session, ordered from small to large based on time.
- **lastName**: Surname or last name of the user.
- **length**: Length of the song in seconds.
- **Level**: Indicates whether the user is a paid user.
- **location**: User's location.
- **method**: HTTP method used to access web pages (e.g., PUT or GET).
- **page**: Type of page or action being performed.
- **registration**: Timestamp representing the user's registration point in time.
- **sessionId**: Session ID used to identify a single login session.
- **song**: Name of the song being played or interacted with.
- **status**: HTTP page return code (e.g., 200, 307, 404).
- **ts**: Timestamp of the log entry.
- **UserAgent**: Information about the client's browser or user agent.
- **UserId**: Unique identifier for the user.

## Libraries & Applications
### 1. Local machine using Python 3.7 or above:

- **pyspark.sql**
- **pyspark.ml**
- **pandas**
- **numpy**
- **matplotlib**

### 2. AWS EMR cluster using PySpark kernel:
<div align="center">
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/AWS_config.png" width="100%">
</div>

- **Hadoop 3.2.1**
- **Hive 3.1.2**
- **Jupyter Enterprise Gateway 2.1.0**
- **JupyterHub 1.1.0**
- **Pig 0.17.0**
- **Spark 7.0.1**

## Conclusions
Apache Spark proves its prowess in efficient big data analysis by drastically reducing processing time through distributed computing. Remarkably, it takes **only 10 seconds to load a massive 12GB** dataset into memory. The frequency of Sparkify service usage, as reflected in metrics like `session_gap`, `total_session`, and `interactions`, alongside user activity on the platform - especially `thumbs_down` - emerge as significant factors influencing churn prediction. 

<div align="center">
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/LR_coef.png" width="100%">
</div>

<div align="center">
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/RF_Feat.png" width="100%">
</div>

<div align="center">
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/model.png" width="100%">
</div>

<div align="center">
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/LR_weight.png" width="100%">
</div>

## Licensing, Authors, Acknowledgements
I would like to extend my sincere gratitude to Sparkify for their contribution in making this valuable resource available to the public. A special acknowledgment goes to Udacity for their exceptional guidance throughout this project. Feel free to utilize the contents of this work, and when doing so, please remember to appropriately attribute the contributions of myself, and/or Sparkify. 

For detailed discussion, follow this medium blog post: [Link](https://medium.com/@LobsterTing/spark-ml-with-aws-emr-acdfab30ef01)

