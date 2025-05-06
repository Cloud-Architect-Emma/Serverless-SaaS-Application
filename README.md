# Book Recommendation API - Serverless SaaS Application

This project is a fully serverless Book Recommendation API built on AWS using **Terraform**, **Lambda**, **API Gateway**, **DynamoDB**, and **S3**. It allows users to browse books by genre, view thumbnails, and get redirected to Amazon via a “Learn More” button. It also features a basic “Add to Cart” simulation.

---

## Features

- **Infrastructure-as-Code (IaC)** using Terraform for full AWS deployment
- **Serverless Backend** with AWS Lambda and API Gateway
- **API Endpoints** to fetch all books and personalized recommendations
- **DynamoDB Tables** for `Books` and `UserPreferences`
- **S3 Static Website** for serving the frontend and book thumbnails
- **CloudWatch Logs** for monitoring and debugging Lambda/API Gateway
- **IAM Roles & Permissions** for secure access control
- **Responsive Frontend** using HTML and Tailwind CSS

---

## Architecture

![Architecture](./architecture/architecture.png)

### Components:

- **API Gateway**: Handles HTTP requests and routes to Lambda
- **Lambda**: Serverless functions that process logic and access DynamoDB
- **DynamoDB**: NoSQL database storing book metadata and user preferences
- **S3**: Public bucket serving static site and book thumbnails
- **CloudWatch**: Logs Lambda and API activity for debugging

---

## IAM Policies Used

The following AWS-managed IAM policies were used in this project:

| Policy Name                           | Type         | Purpose                                       |
|--------------------------------------|--------------|-----------------------------------------------|
| `AmazonAPIGatewayInvokeFullAccess`     | AWS managed  | Invoke API Gateway endpoints                  |
| `AmazonAPIGatewayPushToCloudWatchLogs` | AWS managed  | Enable API Gateway logging to CloudWatch      |
| `AmazonDynamoDBFullAccess`             | AWS managed  | Full access to DynamoDB tables                |
| `AmazonS3ReadOnlyAccess`               | AWS managed  | Read access to book thumbnails in S3          |
| `CloudWatchLogsFullAccess`             | AWS managed  | Monitor Lambda/API Gateway logs               |
| `AWSLambdaBasicExecutionRole`          | AWS managed  | Required for Lambda logging to CloudWatch     |

---

## API Endpoints

- `GET /books`  
  Returns all available books

- `GET /books/preferences?genre=Fiction`  
  Returns books filtered by user preference (e.g., genre)

These endpoints are served through **Amazon API Gateway** and connected to **AWS Lambda** functions.

---

## DynamoDB Tables

- **Books**
  - Fields: `title`, `author`, `genre`, `amazonLink`, `thumbnail`
- **UserPreferences**
  - Fields: `userId`, `preferredGenre`

---

## Screenshots

| Screenshot | Description |
|------------|-------------|
| ![CloudWatch](https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/CloudWatch%20book%20thumbnails.JPG) | CloudWatch Logs for Lambda/API |
| ![Book Thumbnails Web](https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/book%20thumbnails%20web.JPG) | Static Website hosted on S3 |
| ![S3 Images](https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/s3%20book%20thumbnails%20images.JPG) | Book thumbnail images in S3 |
| ![API Gateway](https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/api%20book%20thumbnails.JPG) | API Gateway setup for endpoints |
| ![DynamoDB](https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/dynamodb%20book%20thumbnails.JPG) | Book and UserPreferences tables |
| ![Lambda Functions](https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/lambdas%20book%20thumbnails.JPG) | Lambda functions to serve APIs |
| ![Lambda Permission](https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/lambda%20permission%20book%20thumbnails.JPG) | Lambda execution roles and permissions |
| ![Lambda Code](https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/lambda%20book%20thumbnails.JPG) | Sample Lambda code |



---

## Deployment Notes

- **Terraform** used to provision:
  - Lambda functions and roles
  - API Gateway and routes
  - DynamoDB tables
  - S3 buckets for hosting and assets
  - IAM policies and roles
- Frontend hosted via **S3 Static Website**
- Public bucket used: `emma-book-thumbnails`

---

## Developed By
**Emma** 

---

## License

This project is licensed under the [MIT License](LICENSE).
