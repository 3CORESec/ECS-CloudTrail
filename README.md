# CloudTrail-ECS-Pipeline
Elastic Ingest Pipeline mapped to ECS and AWS exported fields.

## Project goals
The goal of this project is to create an ingestion pipeline for Elasticsearch while staying in sync with Elastic in their developments of mapping AWS CloudTrail data fields to [ECS](https://www.elastic.co/guide/en/ecs/current/index.html) or by defining them as [AWS-specific](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) *(also known as export fields)*. 

The usage of this pipeline is particularly useful when integrating this normalization with [Functionbeat](https://www.elastic.co/beats/functionbeat).

# Pipeline Reference Fields

| Source Field                                        | ECS Field           | EXPORTED                                                       | Category                                                                                     |
|-----------------------------------------------------|---------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------|
| awsRegion                                           | cloud.region        |                                                                | [ECS - Cloud Fields](https://www.elastic.co/guide/en/ecs/current/ecs-cloud.html)             |
| eventID                                             | event.id            |                                                                | [ECS - Event Fields](https://www.elastic.co/guide/en/ecs/current/ecs-event.html)             |
| eventName                                           | event.action        |                                                                | [ECS - Event Fields](https://www.elastic.co/guide/en/ecs/current/ecs-event.html)             |
| eventSource                                         | event.provider      |                                                                | [ECS - Event Fields](https://www.elastic.co/guide/en/ecs/current/ecs-event.html)             |
| eventTime                                           | @timestamp          |                                                                | [ECS - Base Fields](https://www.elastic.co/guide/en/ecs/current/ecs-base.html)               |
| eventType                                           |                     | aws.cloudtrail.event_type                                      | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| recipientAccountId                                  |                     | aws.cloudtrail.recipient_account_id                            | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| requestID                                           |                     | aws.cloudtrail.request_id                                      | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| requestParameters                                   |                     | aws.cloudtrail.request_parameters                              | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| responseElements                                    |                     | aws.cloudtrail.response_elements                               | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| sourceIPAddress                                     | source.address      |                                                                | [ECS - Source Fields](https://www.elastic.co/guide/en/ecs/current/ecs-source.html)           |
| sourceIPAddress                                     | source.geo          |                                                                | [ECS - Geo Fields](https://www.elastic.co/guide/en/ecs/current/ecs-geo.html)                 |
| userIdentity.accessKeyId                            |                     | aws.cloudtrail.user_identity.access_key_id                     | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| userIdentity.accountId                              | cloud.account.id    |                                                                | [ECS - Cloud Fields](https://www.elastic.co/guide/en/ecs/current/ecs-cloud.html)             |
| userIdentity.arn                                    |                     | aws.cloudtrail.user_identity.arn                               | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| userIdentity.invokedBy                              |                     | aws.cloudtrail.user_identity.invoked_by                        | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| userIdentity.principalId                            | user.id             |                                                                | [User Fields](https://www.elastic.co/guide/en/ecs/current/ecs-user.html)                     |
| userIdentity.sessionContext.attributes.creationDate |                     | aws.cloudtrail.user_identity.session_context.creation_date     | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| user.sessionContext.attributes.mfaAuthenticated     |                     | aws.cloudtrail.user_identity.session_context.mfa_authenticated | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| userAgent                                           | user_agent.original |                                                                | [ECS - User Agent Fields](https://www.elastic.co/guide/en/ecs/current/ecs-user_agent.html)   |
| vpcEndpointId                                       |                     | aws.cloudtrail.vpc_endpoint_id                                 | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| errorMessage                                        |                     | aws.cloudtrail.error_message                                   | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| eventVersion                                        |                     | aws.cloudtrail.event_version                                   | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| sharedEventId                                       |                     | aws.cloudtrail.shared_event_id                                 | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| userIdentity.type                                   |                     | aws.cloudtrail.user_identity.type                              | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| userIdentity.userName                               | user.name           |                                                                | [ECS - User Fields](https://www.elastic.co/guide/en/ecs/current/ecs-user.html)               |
| apiVersion                                          |                     | aws.cloudtrail.api_version                                     | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| managementEvent                                     |                     | aws.cloudtrail.management_event                                | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| readOnly                                            |                     | aws.cloudtrail.read_only                                       | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| resources.ARN                                       |                     | aws.cloudtrail.resources.arn                                   | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| resources.accountId                                 |                     | aws.cloudtrail.resources.account_id                            | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |
| resources.type                                      |                     | aws.cloudtrail.resources.type                                  | [AWS Fields](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) |

# Pipeline installation

## Integration with Functionbeat

# Additional fields?
We're constantly analyzing AWS CloudTrail data for any missing fields *(not present in the reference table)*. If you'd like to help, please open an issue here, or directly with Elastic and let us know. 
