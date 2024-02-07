# AWS Step Functions State Machine and Lambda Functions Deployment

This repository contains code for an AWS Step Functions state machine and associated Lambda functions for handling purchase and refund processes.

## State Machine Description
The state machine is designed to handle two types of transactions: "PURCHASE" and "REFUND". It utilizes AWS Step Functions to orchestrate the workflow. The state machine has the following structure:

## Choice State (Choice): This state checks the type of transaction and routes it to the appropriate handler based on the value of $.type.

Purchase Handler (Purchase Handler): 

If the transaction type is "PURCHASE", this state invokes the Purchase Handler Lambda function to process the purchase. It handles potential errors using retries and then moves to the Result Handler state.

## Result Handler (Result Handler): 

This state invokes the Result Handler Lambda function to process the result of the transaction. It marks the end of the state machine execution.

## Refund Handler (Refund Handler): 
If the transaction type is "REFUND", this state invokes the Refund Handler Lambda function to process the refund. It also handles potential errors using retries and then moves to the Result Handler state.

## Lambda Functions

## Purchase Handler
The Purchase Handler Lambda function processes purchase transactions. It is triggered by the state machine and returns a result indicating the success of the purchase process.

## Refund Handler
The Refund Handler Lambda function processes refund transactions. It is triggered by the state machine and returns a result indicating the success of the refund process.

## Result Handler
The Result Handler Lambda function processes the result of both purchase and refund transactions. It is invoked by both the Purchase Handler and Refund Handler states to handle the final result of the transaction.

## Usage
Follow these steps to deploy the state machine and Lambda functions:

## Deploy the State Machine:

1. Use the AWS Management Console or AWS CLI to deploy the state machine defined in the provided JSON configuration file.
2. Navigate to the AWS Step Functions service.
3. Create a new state machine and upload the JSON configuration file.
4. Review and confirm the state machine configuration.

## Deploy the Lambda Functions:

1. Navigate to the AWS Lambda service in the AWS Management Console.
2. Create a new Lambda function for each handler (Purchase Handler, Refund Handler, Result Handler).
3. Copy the code provided for each Lambda function into the corresponding function editor.
4. Configure the Lambda functions with appropriate permissions and execution roles.
5. Note down the ARN (Amazon Resource Name) of each Lambda function for later use.

## Update State Machine Configuration:

1. Update the ARNs of the Lambda functions in the state machine JSON configuration file with the ARNs of the deployed Lambda functions.
Replace the placeholders in the FunctionName fields of the JSON configuration file with the actual ARNs of the corresponding Lambda functions.

## Testing:

1. Trigger the state machine with appropriate input data to test the workflow.
2. Verify that the state machine executes successfully and the Lambda functions are invoked as expected.
3. Check the output of the state machine execution to ensure that the transaction processing is working correctly.
