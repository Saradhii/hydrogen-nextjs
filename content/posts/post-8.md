---
title: "How install Elastic Search (self hosted) in AWS EC2 instance from scratch"
date: 2022-09-23T05:00:00Z
image: /images/posts/elastic.jpg
categories:
   - Technology
draft: false
---

Elasticsearch is an open-source search and analytics engine widely used for full-text search and real-time analytics. It is known for its speed, scalability, and flexibility. Installing Elasticsearch on an EC2 instance is a popular choice for those looking to leverage the power of Elasticsearch in a cloud environment. In this article, we will walk you through the step-by-step process of installing Elasticsearch on an EC2 instance.

Prerequisites: <br></br>
1)An EC2 instance running an Amazon Linux or another compatible operating system.<br></br>
2)Java Runtime Environment (JRE) version 8 or higher.

#### Step 1: Update the system

First, we need to update the operating system packages and dependencies to ensure that everything is up-to-date. To do this, run the following commands in your EC2 instance terminal:

> sudo yum update -y


#### Step 2: Install Java

Elasticsearch requires Java to run. To install Java on the EC2 instance, use the following command:

>sudo yum install java-1.8.0-openjdk -y

#### Step 3: Download and install Elasticsearch

To download the Elasticsearch package, we will use the wget command to retrieve the latest version of Elasticsearch:

>wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.14.2-x86_64.rpm

After downloading the Elasticsearch package, we need to install it using the rpm command:

>sudo rpm -ivh elasticsearch-7.14.2-x86_64.rpm

#### Step 4: Configure Elasticsearch

Next, we need to configure Elasticsearch to run properly. The Elasticsearch configuration file is located at /etc/elasticsearch/elasticsearch.yml. To edit the file, use the following command:

>sudo nano /etc/elasticsearch/elasticsearch.yml

In this file, you can configure various Elasticsearch settings, such as network host, cluster name, and node name. For example, you can change the network host by uncommenting the following line and setting it to the IP address of your EC2 instance:

>network.host: YOUR_EC2_INSTANCE_IP_ADDRESS

#### Step 5: Start Elasticsearch
To start Elasticsearch, use the following command:
>sudo service elasticsearch start

You can check the status of Elasticsearch using the following command:
>sudo service elasticsearch status

#### Step 6: Test Elasticsearch
To test Elasticsearch, you can use the curl command to query Elasticsearch for information about the cluster. For example, you can use the following command to get information about the nodes in the cluster:
>curl -X GET "http://localhost:9200/_cat/nodes?v&pretty"

If Elasticsearch is running properly, you should see a response with information about the nodes in the cluster.

Conclusion:
In this article, we have gone through the steps required to install Elasticsearch on an EC2 instance. By following these steps, you can leverage the power of Elasticsearch for full-text search and real-time analytics in the cloud. Once Elasticsearch is up and running, you can start using it to store, search, and analyze your data.
