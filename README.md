

# Host a serverless web app on AWS S3 bucket.

A brief description on how to connect your static website hosted on Aws s3 with the help of Aws CodePipeline.


## Lab Overview


![alt text](https://github.com/saqib59/portfolio_aws/blob/main/assets/img/local_to_aws.png?raw=true)

![alt text](https://github.com/saqib59/portfolio_aws/blob/main/assets/img/lamda_apigateway.png?raw=true)


## Code Pipeline and S3 Bucket

To push your code from GitHub to an Amazon S3 bucket, you can use the AWS CodePipeline service. Here's an outline of the steps you can follow:

- Set up an AWS account and create an IAM user with permissions to access S3 and CodePipeline.
- Create an S3 bucket to store your code.
- Enable static website hosting for the bucket. To enable static website hosting, you will need to set the bucket's static website hosting configuration and specify the name of the index document and the error document.
- Connect your GitHub repository to CodePipeline by following the instructions in the AWS documentation.
- Create a new CodePipeline and choose GitHub as the source provider.
- In the pipeline configuration, specify the name of the S3 bucket you created as the destination for your code.
- Configure the build and deployment stages of your pipeline as needed. You may need to create an Amazon Elastic Container Registry (ECR) repository and an Amazon Elastic Container Service (ECS) cluster to deploy your code to.
- Run the pipeline to deploy your code from GitHub to S3.

## Route 53

- To redirect it to a specific domain you can add an record for your s3 bucked in your route 53 dashboard.

- You must give the bucket the same name as the record that you want to use to route traffic to the bucket. For example, if you want to route traffic for example.com to an S3 bucket that is configured for website hosting, the name of the bucket must be example.com.

Alternatively, you can also use the AWS CLI to sync the contents
of your GitHub repository to an S3 bucket. To do this, you
can use the aws s3 sync command and specify the path to your 
local repository as the source and the name of your S3 bucket
as the destination.




For example:

```bash
  aws s3 sync path/to/local/repository s3://my-bucket

```

This will upload all the files in your repository to the S3 bucket.



## Lambda

 To create a Lambda function that can submit a contact form in an S3 bucket, you can follow these steps:

- In the AWS Management Console and navigate to the Lambda service.
- Click the "Create function" button.
- Select the "Author from scratch" option.
- Give your function a name and select the runtime that you want to use (e.g. Node.js, Python, etc.).
- In the "Execution role" section, choose an IAM role that allows your function to access the required AWS services (e.g. Amazon S3, Amazon SES, etc.).
- Click on the "Create function" button to create your function.
- To test your function, you can use the "Test" button in the AWS Lambda console.



Note: Some of the above steps may vary depending on your specific requirements and the runtime you have chosen for your function.


## API Gateway

1- Create an API Gateway
- Navigate to the API Gateway console.
- Click the "Create API" button.
- Choose the "REST" protocol and the "New API" option.
- Provide a name for your API and click the "Create API" button.

2- Create a resource and method for your API:

- In the "Resources" panel on the left side of the screen, click the "Actions" dropdown and choose "Create Resource".
- Provide a name for your resource and click the "Create Resource" button.
- In the "Actions" dropdown for your new resource, choose "Create Method".
- From the "Method dropdown, choose "POST" and click the checkmark to create the method.
- In the "Integration type" dropdown, choose "Lambda Function" and select the Lambda function created in previous step.
- Click the "Save" button to create the method.

3- Deploy & Test

- In the "Actions" dropdown for your API, choose "Deploy API". In the "Deployment stage" dropdown, 
  choose "[New Stage]" and provide a name for your stage. Click the "Deploy" button to deploy your API.

- In the "Stages" panel on the left side of the screen, click the name of your stage. Copy the "Invoke URL" 
  for your stage. Use this URL in an HTML form on your static website to submit the contact form data to your Lambda function via the API Gateway.






## Feedback

I hope this helps. If you have any feedback, please reach out to me at saqibali80400@gmail.com



  

