# AWS CloudTrail pipeline
Elastic Ingest Pipeline mapped to ECS and AWS exported fields.

## Project goals
The goal of this project is to create an ingestion pipeline for Elasticsearch while staying in sync with Elastic in their developments of mapping AWS CloudTrail data fields to [ECS](https://www.elastic.co/guide/en/ecs/current/index.html) or by defining them as [AWS-specific](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) *(also known as export fields)*. 

The usage of this pipeline is particularly useful when integrating this normalization with [Functionbeat](https://www.elastic.co/beats/functionbeat).

# Pipeline installation
![alt text](./imgs/put-pipeline.png "put-pipeline")

# Pipeline Reference Fields
Formatting of the table in Github didn't look so good, so we moved the reference table to a [Google Sheet](https://docs.google.com/spreadsheets/d/1rtyP4s3R5iu55ob2uNWfbUoUO_GGBNOUV-PiHcCEMjI).

## Integration with Functionbeat
Just add the following to your **functionbeat.yml**:

![alt text](./imgs/fb-config.png "fb-config.png")

# Additional fields?
We're constantly analyzing AWS CloudTrail data for any missing fields *(not present in the reference table)*. If you'd like to help, please open an issue here, or directly with Elastic and let us know. We also make sure that the pipeline is in sync with the awesome work done by Elastic.
