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
