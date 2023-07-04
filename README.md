# Telemetry
In the context of cloud computing, telemetry refers to the process of collecting and analyzing data from cloud-based resources and services. It involves the gathering of various performance metrics, logs, and other relevant data to monitor and optimize the operation of cloud-based applications, infrastructure, and services.


Cloud telemetry for storage involves monitoring and analyzing data related to storage resources and services in a cloud environment. It provides insights into the performance, capacity, availability, and usage of cloud storage solutions.






![telemetry](https://github.com/ambiknai/telemetry/assets/16678376/caf50499-c5a9-49bb-806d-5927f660a8c4)

# Proposal

Individual storage components will have metrics pushed to endpoint. Here, storage API microservice will be the endpoint where metrics will be pushed by each storage service. Metrics format for each component will remain the same.Once storage API microservice receives metrics from each storage service, it is pushed to target like Segment.

# Challenges

1. Chances are there that Microservice might get busy and is unable to receive metrics. Inorder to make sure , metrics pushed at this point of time are not lost we must have a cache in place

2. Another possibility is that service might get busy and unable to push metrics to Microservice. There must be a buffering in service end so that metrics can be pushed even in such conditions.

3. Limited access to sensitive information like User details for security reasons.
  
4. Any hosted/satellite environment will connect back to API service and will share metrics ro service.  API will be exposed by microservice which will only be available to storage components. Hence proper authentication must be in place. Additional endpoint available to all regions must be exposed which will be used by segment.






