- The AWS equivalent of Datadog for monitoring and observability is `Amazon CloudWatch` and `AWS X-Ray`. These services provide similar features to Datadog, including metrics, logs, tracing, and alerting.
1. **AWS CloudWatch** (Metrics & Logs)
  - Equivalent to: Datadog Metrics & Logs
  - AWS CloudWatch collects and analyzes logs, monitors infrastructure and applications, and provides alerting.
- **Key Features**
  -  Metrics & Dashboards – Monitor CPU, memory, and network usage
  -  Log Aggregation – Collect logs from AWS Lambda, EC2, ECS, API Gateway
  - Alarms & Notifications – Set up alerts with SNS, Slack, or email
  - Event-Driven Actions – Automatically trigger Lambda on log anomalies
- **Example:** Monitor AWS Lambda Logs
  - Enable ***CloudWatch Logs*** in the AWS Lambda function.
  - View logs in ***AWS Console → CloudWatch Logs → Log Groups***.
  - Query logs using ***CloudWatch Logs Insights***:
  ```
  filter @message like "ERROR"
  | stats count(*) by @logStream
  ```
2. **AWS X-Ray (Distributed Tracing)**
- Equivalent to: Datadog APM (Application Performance Monitoring)
- AWS X-Ray traces requests across AWS services and helps debug performance bottlenecks.
- **Key Features**
  - Distributed Tracing – Tracks requests from API Gateway → Lambda → DynamoDB
  - Latency Analysis – Identifies slow-performing AWS resources
  - Service Maps – Visual representation of AWS service interactions
- **Example:** Enable X-Ray in AWS Lambda
  1. Add X-Ray SDK:
  ```
  pip install aws-xray-sdk
  ```
  2. Modify Lambda function:
  ```
  from aws_xray_sdk.core import patch_all
  patch_all()
  
  def lambda_handler(event, context):
      return {"statusCode": 200, "body": "Tracing with X-Ray!"}
  ```
- View traces in AWS Console → X-Ray → Service Map.
