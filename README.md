h1.Setting up the Apache Kafka ecosystem locally

To set up the Apache Kafka ecosystem locally, we will use Docker. The docker-compose file for all the required components and configurations can be found in the chapter's GitHub workspace under resources: https://github.com/PacktPublishing/Building-Microservices-with-Micronaut/blob/master/Chapter05/micronaut-petclinic/pet-clinic-reviews/src/main/resources/kafka-zookeeper-kafdrop-docker/docker-compose.yml.

Perform the following steps to install and set up Apache Kafka:

Download the docker-compose file from the aforementioned URL.
Open the GitBash terminal.
Change the directory to where you have placed the docker-compose file.

Run the docker-compose up command in the GitBash terminal.
As a result of following these instructions, Docker will install Zookeeper, Apache Kafka, and Kafdrop. Kafdrop is an intuitive admin GUI for managing Apache Kafka. In the following section, we will verify their installation.

Testing the Apache Kafka ecosystem setup

To test whether the Apache Kafka ecosystem is installed successfully, perform the following steps:

Open the GitBash terminal and run the following command:
winpty docker exec -it kafka bash
Change the directory to opt/bitnami/kafka/bin/.
Add a topic stream by running the following in the GitBash terminal:
command ./kafka-topics.sh --bootstrap-server kafka:9092 --create --partitions 3 --replication-factor 1 --topic foo-stream
To add a message to the topic, run the following in the GitBash terminal:
command ./kafka-console-producer.sh --broker-list kafka:9092 --topic foo-stream
A terminal prompt will appear, type hello-world!, and then hit Enter.
Press Ctrl + D, which should successfully add the event to the topic.
By following these instructions, we added a foo-stream topic and added a message to this topic. To see this topic stream, we can open Kafdrop by opening http://localhost:9100/ in a browser window. Refer to the following screenshot:

Figure 5.6 – Kafdrop showing foo-stream topic messages

Kafdrop provides an intuitive GUI for viewing and managing all the Apache Kafka streams. In the previous screenshot, we can see the messages inside the just created foo-stream.
