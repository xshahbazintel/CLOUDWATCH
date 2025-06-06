sns:
create topic
subscripe to that topic



Metric and metric dimension
builtin and custom metrics usage metrics
metric granularity metric aggregation


Alarm Anatomy:
    Alarm Name: Name for the alaram
    Metric: cpu/memory
    statistic: avg/min/max
    threshold: value at which alaram should trigger
    period: duration for which memory should be evaluated, 1 min, 5 mins, 1hr 
    evaluation period: no of consecutive times that alarm should breach 
    datapoints to alarm 
    comparitive operator: greater than, less than , equal
    alarm actions: what should the alarm do, send notification to sns


stages in creating alarm:

1. Metric: 
    select namespace such as ec2, rds
    give name 
    select the name of instance in rds, ec2 if ec2 then this is instance name
    threshold: value to which alaram should trigger 90 to 95 Percent
    period: timeperiod for which evaluation is to be done
2. Conditions:
    type of threshold
    conditions 
    value
3. Actions
   what should happen if above values met, should it raise alarm or insufficient data or ok
   send notification to sns or lambda or other services
   endpoint arn

States of alarm
OK: The metric is within defined state, assume cpu utilisation is less than 90%
Alaram: Metrics has breached threshold, assume cpu utilisation is over than 90%
Insufficient data: Metric has just entered into alaram state, but it has not triggered alaram because i will wait for some more time to check if metrics has really breached.


Composite Alarms:
when you have multiple alarms on a single instance instead of having mulitiple actions, you can group all these alarms and have a single action on all these alarms