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

## Both Amazon CloudWatch and AWS X-Ray are monitoring and observability services :
| Amazon CloudWatch | AWS X-Ray |
| ----------------- | --------- |
|Primarily used for monitoring AWS resources and applications. It collects and tracks metrics, logs, and events, allowing users to set up alarms and dashboards for operational insights. | Focuses on tracing application requests as they flow through different services. It helps in analyzing performance bottlenecks, latency issues, and debugging distributed applications. |
| Works with logs, metrics, and events from AWS services, applications, and infrastructure. | X-Ray: Captures traces (end-to-end request flow) and visualizes how different services interact. |
| - Monitoring resource usage (CPU, memory, network, etc.). - Setting up alarms and automated actions. | - Debugging microservices-based architectures. - Identifying performance bottlenecks. - Tracing API requests and response times across services. |
| Uses dashboards, graphs, and logs to provide system-wide monitoring. | Offers a service map that shows how different components interact in a request flow. |
| Can integrate with AWS Lambda, EC2, ECS, EKS, RDS, and other AWS services for monitoring. | Works well with microservices, containerized applications, AWS Lambda, and API Gateway to provide distributed tracing. |
| Pricing is based on metrics, logs, and events ingested and stored. | Pricing is based on the number of traces recorded and analyzed. |
| Use CloudWatch when you need high-level system monitoring, infrastructure insights, and alerts. | Use X-Ray when you need detailed request tracing, performance analysis, and debugging for microservices. |
