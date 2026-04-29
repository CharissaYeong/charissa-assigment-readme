# Assignment 2.12

# Given a Lambda function that is triggered upon the creation of files in an S3 bucket, answer the following:
  1) What is the purpose of the execution role on the Lambda function?
  2) What is the purpose of the resource-based policy on the Lambda function?
  3) If the function is needed to upload a file into an S3 bucket, describe (i.e no need for the actual policies)
  4) What is the needed update on the execution role?
5) What is the new resource-based policy that needs to be added (if any)?


## 1. What is the purpose of te 
The execution role defines what the Lambda function is allowed to do during execution.  
It acts as the function’s identity and grants permissions to access AWS services such as CloudWatch or S3.

---

## 2. Purpose of the Resource-Based Policy
The resource-based policy specifies who or what is allowed to invoke the Lambda function.  
In this scenario, it allows the S3 bucket to trigger the function when new files are created, while preventing unauthorized invocations.

---

## 3. If the Function Needs to Upload a File to S3
The function’s permissions must be expanded to allow it to perform write operations on an S3 bucket.  
This is because the function is now performing an additional action (uploading data) beyond just being triggered.

---

## 4. Needed Update on the Execution Role
The execution role must be updated to include permission for the following action:

- `s3:PutObject` on the target S3 bucket

This enables the Lambda function to upload files to the specified bucket.

---

## 5. New Resource-Based Policy Requirement
No new resource-based policy is required.

Resource-based policies only control who can invoke the Lambda function.  
Since the Lambda function itself is initiating the upload to S3, it relies entirely on its execution role for permission.
