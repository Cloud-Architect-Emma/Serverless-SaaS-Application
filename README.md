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
| <img src="https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/CloudWatch%20book%20thumbnails.JPG" width="300" /> | CloudWatch Logs for Lambda/API |
| <img src="https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/book%20thumbnails%20web.JPG" width="300" /> | Static Website hosted on S3 |
| <img src="https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/DynamoDB%20book%20thumbnails.JPG" width="300" /> | Book and UserPreferences tables |
| <img src="https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/Lambda%20book%20thumbnails.JPG" width="300" /> | Lambda functions to serve APIs |
| <img src="https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/Lambda%20permission%20book%20thumbnails.JPG" width="300" /> | Lambda execution roles and permissions |
| <img src="https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/Lambdas%20book%20thumbnails.JPG" width="300" /> | Lambda functions to serve APIs |
| <img src="https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/S3%20book%20thumbnails%20images.JPG" width="300" /> | Book thumbnail images in S3 |
| <img src="https://github.com/Cloud-Architect-Emma/Serverless-SaaS-Application/raw/main/assets/screenshots/API%20book%20thumbnails.JPG" width="300" /> | API Gateway setup for endpoints |


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
