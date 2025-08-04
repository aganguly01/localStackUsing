# Welcome to your CDK TypeScript project

This is a blank project for CDK development with TypeScript.

The `cdk.json` file tells the CDK Toolkit how to execute your app.

## Useful commands

* `npm run build`   compile typescript to js
* `npm run watch`   watch for changes and compile
* `npm run test`    perform the jest unit tests
* `npx cdk deploy`  deploy this stack to your default AWS account/region
* `npx cdk diff`    compare deployed stack with current state
* `npx cdk synth`   emits the synthesized CloudFormation template

# sns-eventbridge-sqs LocalStack CDK Project

This project demonstrates an event-driven architecture using AWS CDK, LocalStack, and AWS services:

- **SNS Topic** triggers a Lambda function
- Lambda forwards events to a custom EventBridge Bus
- EventBridge routes transformed events to a Destination SQS Queue

All deployed locally using **LocalStack** for fast offline development and testing.

---

## Prerequisites

- [Node.js](https://nodejs.org/) (v18.x recommended)
- [npm](https://www.npmjs.com/)
- [Docker](https://www.docker.com/get-started) (LocalStack runs inside Docker)
- [LocalStack CLI](https://github.com/localstack/localstack) (v4.x)
- AWS CDK CLI (v2.x)
- [cdk-local](https://github.com/localstack/cdk-local) (CDK wrapper for LocalStack)

---

## Installation

1. **Clone the repo**

   ```bash
   git clone <your-repo-url>
   cd sns-eventbridge-sqs


npm install

localstack start

export AWS_ACCESS_KEY_ID=test
export AWS_SECRET_ACCESS_KEY=test
export AWS_DEFAULT_REGION=us-east-1
export AWS_ENDPOINT_URL=http://localhost:4566

sns-eventbridge-sqs/
├── bin/
│   └── sns-eventbridge-sqs.ts         # CDK app entry point
├── lib/
│   └── sns-eventbridge-sqs-stack.ts  # CDK stack defining SNS, Lambda, EventBridge, SQS
├── lambda-handler/
│   └── index.js                      # Lambda function handler
├── test/
│   └── localstack-test.sh            # Optional test script to send SNS message and check SQS
├── cdk.json
├── package.json
├── tsconfig.json
└── README.md                        # This file

npm install -g aws-cdk-local
cdklocal bootstrap
cdklocal deploy

awslocal sns list-topics

awslocal sqs receive-message \
  --queue-url http://localhost:4566/000000000000/destination-queue \
  --max-number-of-messages 1


cdklocal destroy

localstack stop

