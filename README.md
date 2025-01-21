# AWS Lambda Express.js API

This a simple demonstration how to deploy an Express.js application as a serverless API using AWS Lambda for the CCS3316 - Cloud Insfrastructure module of University.

# Project Structure

app.js / lambda.js: Entry point for the Express application running on AWS Lambda.
routes.js: Defines the API routes.
buildspec.yml: AWS CodeBuild configuration to automate the build and deployment process.
package.json: Node.js project dependencies.

# API Endpoints

* GET /api/v1/: Returns a welcome message.

```json
{ "message": "Hello from Express.js on AWS Lambda!" }
```

* GET /api/v1/hello/:name: Greets a user with their name.
```json
{ "message": "Hello, [name]!" }
```

* POST /api/v1/data: Receives JSON data and echoes it back.

```json
{ "mesage": "Received data successfully!", "data": { ... } }
```

# Setup and Deployment

1. Clone the repository:

```bash
git clone [repository-url]
cd [project-directory]
```

2. Install dependencies:
```bash
npm install
```

3. Create AWS Lambda Function:
    * Set the handler to lambda.handler (points to lambda.js).
    * Link Lambda to an API Gateway for accessing the API.

4. Configure AWS CodeBuild:

    * Set up an AWS CodePipeline that connects to this repository (GitHub) and triggers CodeBuild on each commit.
    * CodeBuild uses buildspec.yml to package the Lambda function and deploy it automatically.

5. Push Changes:

    * Any changes pushed to GitHub will trigger CodeBuild, which packages and deploys your Lambda function.

# AWS CodeBuild & CodePipeline

* buildspec.yml automates:
    * Installing Node.js dependencies.
    * Creating a zip file for Lambda deployment.
    * Updating the Lambda function with the new code.

# Notes
* Node.js Version: Ensure that AWS CodeBuild uses Node.js 20 or any version specified in buildspec.yml.
* API Gateway: An API Gateway needs to be set up in AWS to expose the Lambda functions as RESTful APIs.

