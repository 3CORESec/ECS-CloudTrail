# AWS CloudTrail pipeline for Functionbeat
Elastic Ingest Pipeline mapped to ECS and AWS exported fields.

## Project goals
The goal of this project is to create an ingestion pipeline for Elasticsearch while staying in sync with Elastic in their developments of mapping AWS CloudTrail data fields to [ECS](https://www.elastic.co/guide/en/ecs/current/index.html) or by defining them as [AWS-specific](https://www.elastic.co/guide/en/beats/filebeat/master/exported-fields-aws.html) *(also known as export fields)*. 

The usage of this pipeline is particularly useful when integrating this normalization with [Functionbeat](https://www.elastic.co/beats/functionbeat).

## Why not use the work done by Elastic?
There are two separate tasks that need to be performed in order to normalize a source:

* Define a standard that takes into account the fields as they exist in the origin and how we'd like to transform them *(as well as explaining what information is present in each field)*
* Create a transformation pipeline that, based on the standard, makes those changes
  * The work done by Elastic was to transform AWS CloudTrail -> Elastic AWS Fields -> Elastic Common Schema *(where applicable)*

We're inline with the standards defined by Elastic, however, we chose to transform them differently. 

As intensive users of [Functionbeat](https://www.elastic.co/beats/functionbeat) and since Elastic's focus was on performing transformations through [Filebeat](https://www.elastic.co/beats/filebeat), we applied their methodology but in a different transformation mechanism. If we ever have a transformation that is not in sync or somehow differs from what Elastic is doing, all of them will be clearly identified in the reference table below. 

# Pipeline installation

**Pipeline:** [cloudtrail-ecs.json](./cloudtrail-ecs.json)

![alt text](./imgs/put-pipeline.png "put-pipeline")

# Pipeline Reference Fields
Formatting of the table in Github didn't look so good, so we moved the reference table to a [Google Sheet](https://docs.google.com/spreadsheets/d/1rtyP4s3R5iu55ob2uNWfbUoUO_GGBNOUV-PiHcCEMjI).

## Integration with Functionbeat
Just add the following to your **functionbeat.yml**:

![alt text](./imgs/fb-config.png "fb-config.png")

# Additional fields?
We're constantly analyzing AWS CloudTrail data for any missing fields *(not present in the reference table)*. If you'd like to help, please open an issue here, or directly with Elastic and let us know. We also make sure that the pipeline is in sync with the awesome work done by Elastic.
