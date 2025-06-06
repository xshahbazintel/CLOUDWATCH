Internet Monitoring: 

Internet Monitor provides visibility into how internet issues impact the performance and availability between your applications hosted on AWS and your end users.

synthetic canaries: 

Canaries are scripts written in Node.js, Python, or Java. They create Lambda functions in your account that use Node.js, Python, or Java as the runtime.

Scripts that run on a schedule, to monitor your endpoints and APIs. Canaries follow the same routes and perform the same actions as a customer, which makes it possible for you to continually verify your customer experience even when you don't have any customer traffic on your applications.


they will try to simulate how an actual user logins to system, see the response of applications how an user face and provide feedbacks.
Monitors application and endpoints,  not just health but also performance
integrate with cloudwatch alarms, lambda.


ResourceHealth:
Resource health helps you to discover, manage, monitor, visualize hosts across application.
you can visualize performance with cpu utilisation, with cloodwatch agent installation on host you can visualize memory.
you can filter resources based on tags, auto scaling group, loadbalancer.

Evidently:
Focus on feature experimentation, when you have a new feature and you want to deploy a feature to a set of users and thereby analyse the user behaviour and performance.
you can visualize the impact of new feature on user and how they are interacting with new feature and its performance.


Realtime User Monitoring:
With CloudWatch RUM, you can perform real user monitoring to collect and view client-side data about your web application performance from actual user sessions in near real time.
The data that you can visualize and analyze includes page load times, client-side errors, and user behavior. 
When you view this data, you can see it all aggregated together and also see breakdowns by the browsers and devices that your customers use.

costs associated with cloudwatch:
metrics cost
alarms cost
events cost
dashboards cost
logs cost: logs have ingestion cost and storage cost