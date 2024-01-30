# Building an AWS SNS that sends SMS to your team

## Problem that was Presented 

During the 2024 Winter season we received heavy amounts of snow that forced the schools and some local businesses to close. But a vast majority of the workers for those local businesses did not know. So, many of them had to drive several miles in the inclement weather where they just had to turn back around and drive back home since nothing was open due to the weather. This gave me the idea that a lot of these people could of avoided traveling if the business had a SMS notification system in place that could alert everyone about any closings and changes the business would make during inclement weather.

# AWS Diagram of setting up the SNS

Also the application has two different Spring profiles: `dev` and `prod`. While running `prod`, the application gets all properties(username, password, databasename...) to connect to a RDS database using AWS Secrets Manager for security purposes.

## What is an SNS? 

Amazon Simple Notification Service (Amazon SNS) is a managed service that provides message delivery from publishers to subscribers (also known as producers and consumers). Publishers communicate asynchronously with subscribers by sending messages to a topic, which is a logical access point and communication channel. Clients can subscribe to the SNS topic and receive published messages using a supported endpoint type, such as Amazon Kinesis Data Firehose, Amazon SQS, AWS Lambda, HTTP, email, mobile push notifications, and mobile text messages (SMS). (Treichler & Hardmeier, 2005) 

## Run the application

If you have AWS CLI you can just run:

	git clone https://github.com/codeurjc/spring-cloud-aws-sample
	cd spring-cloud-aws-sample
	mvn package
	cd target
	java -jar spring-cloud-aws-sample-0.2.0-SNAPSHOT.jar \
		--spring.profiles.active=dev \
		--cloud.aws.rds.dbInstanceIdentifier=springaws \
		--cloud.aws.rds.springaws.password=<your password> \
		--cloud.aws.rds.springaws.username=springaws \
		--cloud.aws.rds.springaws.databaseName=springaws



### On AWS (prod)

As you can see is not necessary to put database credentials to run the application, it gets the necessary values from AWS Secret Manager.

### Works cited Links

Treichler, R., & Hardmeier, C. (2005). Schlagwortnormdatei Schweiz für Allgemeine öffentliche Bibliotheken: SNS. Amazon. https://docs.aws.amazon.com/sns/latest/dg/welcome.html 

