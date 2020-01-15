# MSBA 6330 Big Data Analytics

<span style='color:red'>This repository is for the students who take this course only. Please do not distribute.</span>

This repository servers as a single destination for instructions, codes, links to videos, and resources for MSBA 6330 Big Data Analytics (Full Time, Fall 2019). It is updated throughout the semester. 

## <span style='color:red'>[Documents Oraganized By Schedule](schedule.md)</span>

## Syllabus and Homework Related Information

- [Syllabus](syllabus.md)
- [Schedule](schedule.md)
- [FAQs](faqs.md)
- [Homework Guidelines](faqs/homework-guidelines.md)

## Modules

- [Introduction to MSBA6330](01-intro/outline.md)
- [Linux command essentials](00-Linux/outline.md)
    + [Lab 0 - Essential Linux Commands](00-Linux/lab0.md). 
- [Introduction to Hadoop](02-Hadoop/outline.md)
    + [Lab 1: Using HDFS](02-Hadoop/lab01-hdfs.md). 
        + [solution](02-Hadoop/lab01-hdfs-solution.md). 
    + [lab 2: Running a Python MapReduce Job](02-Hadoop/lab02-mapreduce.md).  
        + [solution](02-Hadoop/lab02-mapreduce-solution.md).  
    + [lab 3: Using Sqoop to ingest relational data](02-Hadoop/lab03-scoop.md) 
        + [solution](02-Hadoop/lab03-scoop-solution.md).  
- [Hive 1: Introduction to Hive & Relational Data Analysis](03-Hive1/outline.md)
    + [Lab 6: Running Hive Queries from the Shell, Scripts, and Hue](03-Hive1/lab06-intro.md)
        + [solution](03-Hive1/lab06-intro-solution.md)
    + [Lab 7: Using HiveQL to Analyze an Advertising Campaign](03-Hive1/lab07-hiveql.md)
        + [solution](03-Hive1/lab07-hiveql-solution.md)
    + [Lab 7x: Using Complex Fields in Hive](03-Hive1/lab07x-complexfields.md)
        + [solution](03-Hive1/lab07x-complexfields-solution.md)
- [Hive 2: Hive Data Modeling & Optimization](04-Hive2/outline.md)
    + [Lab 8: Data Management with Hive ](04-Hive2/lab08-datamodel.md)
        + [solution](04-Hive2/lab08-datamodel-solution.md)
	+ [Lab 8x: Using CSV Serde](04-Hive2/lab08x-csvserde.md) 
        + [solution](04-Hive2/lab08x-csvserde-solution.md) 
    + [Lab 9: Hive Optimization](04-Hive2/lab09-hiveopt.md) 
        + [solution](04-Hive2/lab09-hiveopt-solution.md)
- [Hive 3: Hive Text Processing](05-Hive3/outline.md)
    + [Lab 10: Text Analytics with Hive](05-Hive3/lab10-text.md)
        + [solution](05-Hive3/lab10-text-solution.md)
    + [Lab 11: Log Data Analysis with Hive](05-Hive3/lab11-weblog.md)
        + [solution](05-Hive3/lab11-weblog-solution.md)
    + [Lab 12: Work with JSON documents and External Scripts in Hive](05-Hive3/lab12-extension.md)
        + [solution](05-Hive3/lab12-extension-solution.md)
- [Spark 1: Introduction to Apache Spark](10-SparkIntro/outline.md)
    + [Spark Lab 0: Jupyter Notebook tutorial](10-SparkIntro/sparklab00/README.md)
        + [solution](10-SparkIntro/sparklab00/sparklab00-ipython-solution.md)
    + [Spark Lab 1: Explore RDDs Using the Spark Shell](10-SparkIntro/sparklab01/README.md)  
        + [solution](10-SparkIntro/sparklab01/sparklab01-solution.md)  
    + [Spark Lab 1x: Create RDDs](10-SparkIntro/sparklab01x-CreateRdd/README.md)  
        + [solution](10-SparkIntro/sparklab01x-CreateRdd/spark01x-solution.html)  
    + [Spark Lab 2: Use RDDs to Transform a Dataset](10-SparkIntro/sparklab02-RDD-transform/README.md)
        + [solution](10-SparkIntro/sparklab02-RDD-transform/sparklab2-solution.html)
    + [Spark Lab 3: Process Data Files with Spark RDD](10-SparkIntro/sparklab03-RDD-ProcessFiles/README.md)
        + [solution](10-SparkIntro/sparklab03-RDD-ProcessFiles/sparklab3-solution.html)
- [Team Project](team/outline.md)
- [Spark 3: Working with Pair RDDs](13-PairRDD/outline.md)
    + [Spark Lab 4: Use Pair RDDs to join two datasets](13-PairRDD/sparklab04-PairRDD-Join/README.md)
- [Spark 4: Data frames & Spark SQL](14-SparkSQL/outline.md)
    + [Spark Lab 5:Using Spark SQL ](14-SparkSQL/sparklab05-SQL/README.md)
    + [Spark Lab 6:Use Spark SQL to Join and Aggregate Data ](14-SparkSQL/sparklab06-SQL-JoinAgg/README.md)
- [Spark 5: Machine Learning with Spark MLlib](16-SparkML/outline.md)
    + [Spark Lab 7:Using Spark MLlib for Feature Engineering and Prediction ](16-SparkML/sparklab07-MLlib/README.md)
        + [solution](16-SparkML/sparklab07-MLlib/README.md)
    + [Spark Lab 8:Predict bike sharing Using MLlib's pipeline and Gradient-Boosted Trees](16-SparkML/sparklab08-MLlib2/README.md)
        + [solution](16-SparkML/sparklab08-MLlib2/README.md)
- [Spark 6: Spark Streaming](17-SparkStreaming/outline.md)
    + [Spark Lab 9: Streaming Word Count](17-SparkStreaming/sparklab09-StreamWordCount/README.md)
    + [Spark Lab 10: Live Dashboard for Twitter Hashtag](17-SparkStreaming/sparklab10-twitterHashtag)
    + [Spark Lab 11: Structured Streaming](17-SparkStreaming/sparklab11-StructuredStreaming)
- [Cloud Computing & AWS](06-AWS/outline.md)
    + [Lab 12: Create and Launch Amazon EC2 Instance](06-AWS/lab12-aws-ec2/lab12-aws-ec2.md)
        + [solution](06-AWS/lab12-aws-ec2/lab12-aws-ec2-solution.md)
    + [Lab 13: Using AWS EMR to Analyze Web Logs](06-AWS/lab13-aws-emr/lab13-aws-emr.md)
        + [solution](06-AWS/lab13-aws-emr/lab13-aws-emr-solution.md)
- [NoSQL](20-NoSQL/outline.md)
    + [Lab 14: Graph Analytics Using Spark GraphFrames](20-NoSQL/lab14-graphframes/README.md)
    + [Lab 15: Amazon DynamoDB](20-NoSQL/lab15-dynamodb/README.md)

## Homework Assignments

[Homework Guidelines](faqs/homework-guidelines.md)

- [Hw0](homeworks/hw0/homework0.md)
- [Hw1](homeworks/hw1/homework1.md)
- [Hw2](homeworks/hw2/homework2.md)
- [Hw3](homeworks/hw3/homework3.md)
- [Hw4](homeworks/hw4/README.md)
- [Hw5](homeworks/hw5/README.md)
- [Hw6](homeworks/hw6/README.md)
- [Hw7](homeworks/hw7/README.md)
