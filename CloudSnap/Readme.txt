# CloudSnap Image Management System

CloudSnap is an extensive image management system that allows users to upload images, find images based on tags, add or remove tags, and find images based on tags in a provided image. The system leverages Amazon Web Services (AWS), including S3 for storage, API Gateway for REST APIs, AWS Lambda for serverless computing, and a database for storing image metadata.

## Features

1. **Image Upload:** Upload images to an S3 bucket through an API Gateway endpoint or AWS SDKs. On uploading an image, a Lambda function is invoked, which detects objects in the image and saves the detected objects (tags) with the S3 URL in the database.

2. **Find Images by Tags:** Submit a text-based query through an API Gateway to request URLs of images that contain specific tags. The request can be a GET or POST. A Lambda function retrieves the S3 URLs of images matching the tag criteria from the database.

3. **Find Images Based on the Tags of an Image:** Send an image as part of an API call. The system will find the tags in the image and return URLs of images in the storage containing those set of tags.

4. **Manual Tag Addition or Removal:** Using a POST API, users can add or remove tags associated with an image. Depending on the type field in the JSON request, the tags are added or removed.

## Usage

Interact with the system through HTTP requests (GET or POST) to the provided API endpoints. Detailed documentation for each feature, with JSON request/response formats and request parameters, can be found in the specific sections of this README.



