Image Upload and Object Detection:
This repository includes a serverless solution to upload an image to an AWS S3 bucket, which in turn triggers an AWS Lambda function to detect objects in the image and store their details in an AWS database.

How It Works:
Image Upload: The system facilitates the upload of an image to an S3 bucket. The upload operation can be achieved through an API Gateway endpoint (utilizing POST REST APIs) or directly using AWS SDKs such as boto3 for Python.

Trigger Event: When an image is successfully uploaded to the S3 bucket, it triggers an event that invokes a pre-configured AWS Lambda function.

Lambda Function: The invoked Lambda function reads the uploaded image and identifies objects present within the image. To perform object detection, we use the Yolo (You Only Look Once) algorithm, which is fast and accurate.

Object Detection and Tagging: The Lambda function generates a list of detected objects (referred to as "tags") from the uploaded image. It discards any detected objects with an accuracy of detection below a specified threshold (0.6 in our case).

Data Storage: The Lambda function stores the list of detected tags along with the S3 URL of the image in an AWS RDS Databse (In our case we have used postgres) for future queries.

Configuration Files: The Yolo configuration files Along with the dependencies are stored in a separate S3 bucket, which the Lambda function can reference.

Usage
To run the application, you need to upload an image either via the API Gateway endpoint or directly through the AWS SDKs. Once the image is uploaded, it automatically triggers the Lambda function to detect objects in the image.