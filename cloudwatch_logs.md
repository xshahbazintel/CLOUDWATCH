cloudwatch logs: monitor store and allows you to access logs
cloudwatch agents collect and send logs to cloudwatch


Log class
CloudWatch Logs offers two classes of log groups. The Standard log class is a full-featured option for logs that require real-time monitoring or logs that you access frequently. The Infrequent Access log class is a lower-cost option for logs that you access less frequently. It supports a subset of the Standard log class capabilities.

log events:
A log event is a record of some activity recorded by the application or resource being monitored. The log event record that CloudWatch Logs understands contains two properties: the timestamp of when the event occurred, and the raw event message. Event messages must be UTF-8 encoded

log streams:
A log stream is a sequence of log events that share the same source. More specifically, a log stream is generally intended to represent the sequence of events coming from the application instance or resource being monitored. For example, a log stream may be associated with an Apache access log on a specific host. When you no longer need a log stream, you can delete it using the aws logs delete-log-stream command.

log group: 
Log groups define groups of log streams that share the same retention, monitoring, and access control settings. Each log stream has to belong to one log group

pre-ingestion filtering: you can filter data, before sending it to log in cloudwatch, so that you wont end up with huge log data, there by you can reduce costs.
This is done on client side.

MetricFilter:
you can apply this at log groups, create a search filter and create alarms using this if it breaches any threshold.

CloudWatch Agent:
Max size of event should be 256KB, Batch size is 1 MB
Requires SSM 
How to install cloudwatch agent on ec2 server:
1. Attach required Iam role to instance 
   sample iam role
   {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                    "cloudwatch:PutMetricData",
                    "ec2:DescribeVolumes",
                    "ec2:DescribeTags",
                    "logs:PutLogEvents",
                    "logs:DescribeLogStreams",
                    "logs:DescribeLogGroups",
                    "logs:CreateLogStream",
                    "logs:CreateLogGroup"
            ],
            "Resource": ["*"]
        }
    ]
}
2. Install cloudwatch agent on ec2

for debian based instance

wget https://s3.amazonaws.com/amazoncloudwatch-agent/ubuntu/amd64/latest/amazon-cloudwatch-agent.deb

sudo dpkg -i amazon-cloudwatch-agent.deb


3. set up json file

 {
   "metrics": {
     "namespace": "MyCustomNamespace",
     "metrics_collected": {
       "mem": {
         "measurement": [
           "mem_used_percent"
         ],
         "metrics_collection_interval": 1
       },
       "disk": {
         "measurement": [
           "used_percent"
         ],
         "resources": [
           "/"
         ]
       }
     },
     "append_dimensions": {
       "InstanceId": "${aws:InstanceId}"
     }
   }
 }

 cd; sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -s -c file:amazon-cloudwatch-agent.json

 

