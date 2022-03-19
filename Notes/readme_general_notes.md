# Module 16: Big Data Notes

## Four Vs of Big Data

There are four characteristics of big data:

    1. Volume refers to the size of data (e.g., terabytes of product information). For instance, a year's worth of stock market transactions is a large amount of data.
    2. Velocity pertains to how quickly data comes in (customers across the world purchasing every second). As an example, McDonald's restaurants are worldwide with customers buying food at a constant rate, so the data comes in fast.
    3. Variety relates to different forms of data (e.g., user account information, product details, etc.). Consider the breadth of Netflix user information, videos, photos for thumbnails, and so forth.
    4. Veracity concerns the uncertainty of data (e.g., reviews might not be real and could come from bots). As an example, Netflix would want to verify whether users are actively watching the shows, falling asleep, or just playing them in the background.

## Big Data Technologies 
### Hadoop 
We'll start with the three main components of Hadoop:

    - Hadoop Distributed File System (HDFS) is a file system used to store data across server clusters (groups of computers). It is scalable (which means it handles influxes of data), fault-tolerant (handles hardware failure), and distributed (spread across multiple servers connected by a common core).
    - MapReduce is a programming model and processing technique for big data. MapReduce enables processing the large amount of data spread across the cluster in the HDFS by performing the same task for each file system.
    - Yet Another Resource Negotiator (YARN) manages and allocates resources across the clusters and assigns tasks.

### MapReduce Process
MapReduce is used as a means for distributing and processing data on your cluster. 

Let's break down each part of the word count process:

    - Input: The entire file is fed to the word counter.
    - Splitting: Each line of text is separated.
    - Mapping: Each word in every line is assigned a value of 1.
    - Shuffling: The words are combined and organized alphabetically, creating a list of the words' values.
    - Reducing: The list of values are summed for each word.
    - Final Result: The complete list of words and value (counts) are displayed.

### mrjob Library 
Python has a library called mrjob, which stands for "MapReduce job" and it can help us practice MapReduce outside of the Hadoop ecosystem.

- See bacon_counter for more information on mrjob Library 

### Spark 
Apache Spark (Spark) is a unified analytics engine for large-scale data processing. Spark lets you write applications in code that can run on Hadoop. However, Spark doesn't have to run on Hadoop, as it can run in stand-alone mode or in the cloud. Spark can be 100 times faster than Hadoop. Just like Hadoop's MapReduce, Spark works with data spread across a cluster, or a group of computers that work together.

Spark uses in-memory computation instead of a disk-based solution, which means it doesn't need to talk to the HDFS each time and can retain as much as HDFS can in-memory. Spark uses lazy evaluation, which delays the evaluation of an expression or command until the value is needed.

#### Spark Architecture 
The driver, executors, and the cluster manager:

    - The driver is the heart of the application. It is responsible for maintaining the application information; responding to the code or input; and analyzing, distributing, and scheduling work to the executors.
    - The executors perform the code assigned by the driver and then report the state of the computation to the driver.
    - The cluster manager controls the driver and executors and allocates resources to the machines on the Spark applications. The cluster manager is an external service for acquiring resources on the cluster. Spark can either use its own standalone cluster manager that comes standard with Spark or another application (e.g., Apache Mesos, Hadoop YARN).

#### Spark Parallelism 
*Parallelism* in Spark entails running work through a cluster (group of computers) concurrently, instead of performing all work on a single computer. Recall when you and Jennifer were each counting video game reviews in two separate datasets, and you were working parallel to each other. You did not need to wait for Jennifer to do anything before you could start counting your reviews. This is exactly what Spark is doing.

Data is broken into *partitions*, meaning a chunk of your data will sit on a physical machine in your cluster. If your Spark application has three machines, each one of those machines will have a piece of your original dataset. For example, a dataset with 1,000 rows of data might have 334 rows on one machine, 333 on a second, and 333 on a third.

**Note the following guidance when running code in parallel: If there is only one partition but many executors, the parallelism is only one. One machine can only work with one executor.**

- Consider the manager example: If there is only one task but many employees, that task is completed in the time frame that one employee can accomplish it in, and at the pay rate of one employee.

#### Spark API 
##### Language APIs 
Spark can work with: 
- Java
- Python 
- SQL 
- R
*Note:* This course focuses on PySpark (Python Spark package)

##### Data APIs 
Spark supports two different sets of data APIs:

    - Low-level unstructured API is mostly outdated but deals with resilient distributed datasets (RDDs), which are an immutable collection of records that can be operated in parallel. These were part of early versions of Spark.
    - High-level API consists of structured data such as comma-separated values (CSV).

The high-level API consists of three core forms of data that you'll work with in Spark. Notice that all three contain familiar structures:

    - Datasets
    - DataFrames
    - SQL tables and views

When to use low-level APIs: 

    - You need finely tuned control over the data in your clusters that high-level APIs can't provide.
    - Your role involves maintaining legacy code that uses low-level APIs.

## Natural Language Processing (NLP) 
Natural language processing (NLP) is a growing field of study that combines linguistics and computer science for computers to understand written, spoken, and typed natural language. NLP is the process of converting normal language to a machine-readable format, which allows a computer to analyze text as if it were numerical data.

There are a number of important use cases to delve into:

    - Classifying text: For many of the aforementioned use cases to work, a computer must know how to classify a given piece of text. Classification can mean a few different things in NLP. You can have classification of specific words, even specifying what the part of speech is. You can also classify what the text is as a whole.
    - Extracting information: Many NLP tasks require the ability to retrieve specific pieces of information from a given document. Think of the case where we are extracting data from law documents. You might want to extract certain aspects of that document to present good cases.
    - Summarizing a document: Summarization is a key aspect of NLP. It helps solve quite a few different problems. You can essentially create a model that summarizes a given document. This can be helpful to understand the high-level details of law documents, articles, and much more.


