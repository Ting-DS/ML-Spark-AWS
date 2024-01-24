# Big Data Analysis with Spark & AWS EMR
## Build user churn prediction model using 12GB music app user activities data

Analysis process and insights are wrangled in [“my Medium blog post”](https://medium.com/@LobsterTing/spark-ml-with-aws-emr-acdfab30ef01)

A small subset (128MB) of the full data **(12GB)** is used for initial analysis and model development: [sparkify_mini_data_exploration.ipynb](https://github.com/Ting-DS/Spark_AWS_EMR/blob/main/sparkify_mini_data_exploration.ipynb)

Once the features and models are selected, the script can be deployed to AWS EMR to build the model on the full 12GB dataset: [sparkify_AWS_EMR.ipynb](https://github.com/Ting-DS/Spark_AWS_EMR/blob/main/sparkify_AWS_EMR.ipynb)

## Introduction
Sparkify is a music streaming service where users can listen to music, share content, and choose to become paid subscribers. Retaining users is crucial for the company's success, and employing strategies such as offering discounts or implementing other business tactics to potentially churned users can help the company maintain substantial revenue. Therefore, it is imperative to build a machine learning classification model based on user interactions with the platform to **predict churn risk**. Sparkify provides comprehensive user behavior data, totaling **12GB in size**. Analyzing such massive data locally poses a challenge, which is why [Apache Spark](https://spark.apache.org/) is my preferred analysis tool. Deploying data science pipelines on Spark allows us to leverage distributed systems like [HDFS](https://hadoop.apache.org/docs/r1.2.1/hdfs_design.html#Introduction) to enhance the scalability of our models. [Spark SQL and Spark DataFrame](https://spark.apache.org/docs/latest/sql-programming-guide.html) can be utilized for data cleaning, while [Spark ML](https://spark.apache.org/docs/latest/ml-guide.html) supports algorithms like **Logistic Regression, Random Forest, Linear SVM, Gradient Boosting** and other linear expansion models.


<div align="center">

  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/image/AWS_EMR.png" width="100%">

</div>

In this project, we will utilize relevant services on the AWS platform. We'll begin by loading the entire 12GB dataset (around **27,000,000 records with 18 fields**) from [AWS S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html). Subsequently, we will employ cloud services such as [Amazon Elastic MapReduce (Amazon EMR) ](https://www.amazonaws.cn/en/elasticmapreduce/) and [AWS EC2](https://aws.amazon.com/pm/ec2/?trk=36c6da98-7b20-48fa-8225-4784bced9843&sc_channel=ps&ef_id=EAIaIQobChMIqb-QroD3gQMV9y6zAB1ZyAzkEAAYASAAEgLbt_D_BwE:G:s&s_kwcid=AL!4422!3!467723097970!e!!g!!aws%20ec2!11198711716!118263955828) to deploy ETL and ML pipelines, utilizing Spark for data analysis. This approach will significantly improve data processing efficiency and scalability, enabling us to better predict user churn risk and take corresponding measures to retain them.

<div align="center">
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/image/spark_progress.png" width="100%">
</div>

## Data Source

To access full 12GB fataset in AWS S3: "s3n://udacity-dsnd/sparkify/sparkify_event_data.json"

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
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/image/AWS_config.png" width="100%">
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
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/image/LR_coef.png" width="100%">
</div>

<div align="center">
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/image/RF_Feat.png" width="100%">
</div>

<div align="center">
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/image/model.png" width="60%">
</div>

<div align="center">
  <img src="https://github.com/Ting-DS/Spark_Music_App/blob/main/image/LR_weight.png" width="60%">
</div>

## Licensing, Authors, Acknowledgements
I would like to extend my sincere gratitude to Sparkify for their contribution in making this valuable resource available to the public. A special acknowledgment goes to Udacity for their exceptional guidance throughout this project. Feel free to utilize the contents of this work, and when doing so, please remember to appropriately attribute the contributions of myself, and/or Sparkify.


For detailed discussion, follow this Medium blog post: [“Spark ML with AWS EMR”](https://medium.com/@LobsterTing/spark-ml-with-aws-emr-acdfab30ef01)

## Reference
 - [Apache Spark](https://spark.apache.org/)
 - [HDFS](https://hadoop.apache.org/docs/r1.2.1/hdfs_design.html#Introduction)
 - [Spark SQL and Spark DataFrame](https://spark.apache.org/docs/latest/sql-programming-guide.html)
 - [Spark ML](https://spark.apache.org/docs/latest/ml-guide.html)
 - [AWS S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)
 - [Amazon Elastic MapReduce (Amazon EMR) ](https://www.amazonaws.cn/en/elasticmapreduce/) and [AWS EC2](https://aws.amazon.com/pm/ec2/?trk=36c6da98-7b20-48fa-8225-4784bced9843&sc_channel=ps&ef_id=EAIaIQobChMIqb-QroD3gQMV9y6zAB1ZyAzkEAAYASAAEgLbt_D_BwE:G:s&s_kwcid=AL!4422!3!467723097970!e!!g!!aws%20ec2!11198711716!118263955828)
 - [AWS EC2](https://aws.amazon.com/pm/ec2/?trk=36c6da98-7b20-48fa-8225-4784bced9843&sc_channel=ps&ef_id=EAIaIQobChMIqb-QroD3gQMV9y6zAB1ZyAzkEAAYASAAEgLbt_D_BwE:G:s&s_kwcid=AL!4422!3!467723097970!e!!g!!aws%20ec2!11198711716!118263955828)
 - [IAM roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html)


For detailed discussion, follow this medium blog post: [Link](https://medium.com/@LobsterTing/spark-ml-with-aws-emr-acdfab30ef01)

