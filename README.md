# Cloudwatch Monitoring and Alerting with Slack

All our logging and monitoring is handled by CloudWatch. For important metrics, we create CloudWatch Alarms that trigger whenever a metric crosses a defined threshold - for exemple, when a dead-letter queue has a non-zero number of messages. when an alarm triggers, we have CloudWatuch send a notification to an SNS topic.

All our alarms send notificactions to the same topic, which in turn triggers a Post to Slack Lambda. This is a NodeJs or Golang function that reads the notificacion, and calls the Slack API to post a message to an terminal Slack channel.