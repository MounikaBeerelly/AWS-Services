# Azure Cloud Functions

- Azure Functions is a serverless compute service provided by Microsoft Azure that allows you to run event-driven code without provisioning or managing infrastructure.
- You can use Functions to build web APIs, respond to database changes, process IoT streams, manage message queues, and more.
- It automatically scales based on demand and charges only for the execution time used.
### Key Features of Azure Functions
1. **Event-Driven Execution:**
- Functions can be triggered by various events like HTTP requests, queue messages, timers, database changes, and service bus messages.
2. **Scalability & Cost Efficiency:**
- Automatically scales up/down based on workload.
- Pricing is based on execution time and memory usage.
3. **Multiple Language Support:**
- Supports C#, JavaScript/Node.js, Python, Java, TypeScript, PowerShell, Go.
4. **Built-in Integrations:**
- Easily integrates with Azure Storage, Cosmos DB, Event Grid, Service Bus, and more.
5. **Monitoring & Observability:**
- Works with Azure Monitor, Application Insights, Datadog, Splunk, and New Relic.
### Common Use Cases
1. **APIs & Microservices:** Serve REST APIs with HTTP-triggered functions.
2. **Event Processing:** Process messages from Azure Queue Storage or Event Hub.
3. **Data Transformation:** Process and enrich real-time data.
4. **Task Automation:** Automate scheduled jobs (e.g., daily backups).
- **Example:** HTTP-Triggered Azure Function (JavaScript)
  ```
  module.exports = async function (context, req) {
      context.res = {
          status: 200,
          body: "Hello from Azure Function!"
      };
  };
  ```
- Deploy this function, and Azure will provide an endpoint like: `https://<your-function-app>.azurewebsites.net/api/<function-name>`
