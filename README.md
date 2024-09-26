**Stock Market Data Pipeline using Apache Kafka and AWS**

**Overview**
This project simulates a real-time stock market data streaming pipeline using Apache Kafka and various AWS services. The primary objective is to ingest, process, and store stock market data for analysis using tools like AWS Glue and Amazon Athena. This pipeline is scalable and demonstrates a typical architecture for real-time data processing using distributed systems.

**Architecture**
The architecture of the project is shown in the diagram and can be summarized as follows:

![Architecture](https://github.com/user-attachments/assets/233a9c2d-9fc2-475c-b056-3f090dc719bc)


**Producer:**
A Python application simulates stock market data based on a dataset provided in the repository.
The producer uses the Boto3 SDK and Kafka client to publish simulated stock data to the Kafka topic.
The dataset (CSV file) is read and pushed into the Kafka stream in real time.
Kafka:

Apache Kafka is hosted on an EC2 instance and acts as the central message broker for this project.
Kafka manages the real-time streaming data, where the Python app acts as the producer and AWS services act as consumers.

**Consumer:**
The Kafka consumer reads the data from the Kafka topic and stores it in an Amazon S3 bucket for further processing.
AWS Glue Crawler is used to catalog the data stored in S3, enabling it to be queried and processed.
AWS Glue and Athena:

AWS Glue creates a data catalog that stores metadata about the data ingested into S3.
Amazon Athena is used to perform SQL queries on the data catalog for analysis and reporting.
Steps Involved
Simulating Stock Market Data:

The producer application simulates real-time stock market data from a CSV file using a Python script.
The data is sent to a Kafka topic.
Ingesting Data to AWS:

The consumer application listens to the Kafka topic and writes the data to an S3 bucket.
A Glue Crawler is set up to detect new data in the S3 bucket and update the AWS Glue Data Catalog.

**Data Analysis:**
Once the data is cataloged, Amazon Athena can be used to query and analyze the data in near real-time.
You can run SQL queries on the stock market data directly in Athena, without needing to load the data into a separate database.
Dataset
The Stock Market Dataset used for this project is included in this repository as stock_market_data.csv. This dataset is used by the producer application to simulate real-time stock data streaming.

**Requirements**
To replicate or run the project, the following tools and libraries are required:

Apache Kafka: Installed on an EC2 instance or any other server.
Python 3.x: For writing producer/consumer applications.
Kafka-Python: Python client for Kafka (pip install kafka-python).
Boto3: AWS SDK for Python (pip install boto3).
AWS Account: To set up services like S3, Glue, and Athena.
AWS CLI: For interacting with AWS services from the command line.

**How to Run**
Set up Apache Kafka on an EC2 instance or any other server. Create a Kafka topic for streaming stock market data.
Run the Producer: Use the provided Python script to simulate stock market data and produce it to Kafka.
The script reads the stock_market_data.csv file and sends data to the Kafka topic.
Set up AWS S3, Glue, and Athena:
Create an S3 bucket to store the data ingested from Kafka.
Set up a Glue Crawler to detect new data and update the data catalog.
Use Athena to query the data for analysis.
Run the Consumer: The consumer reads messages from the Kafka topic and stores them in the S3 bucket.


