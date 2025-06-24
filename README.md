# IIoT monitoring using Siemens PLC, MQTT, Kafka, Python, MongoDB and ELK stack

IIoT project for data exchange between PLC in OT and IT area with usage of MQTT protocol, Kafka streaming and MongoDB.

### System Diagram
![System Architecture](./docs/project-IIoT-mqtt-kafka-elk-tia-portal.png)

### General Overview
The purpose of this project is to collect data from different sensors, states and devices connected to PLC in OT area.
The collected data are proprocessed in Siemens PLC, converted into JSON structure and published as MQTT message to HiveMQ MQTT Broker.

HiveMQ broker is equipped with Extension for Kafka. This implementation enables seamless integration of MQTT messages from OT into Kafka data streaming.

Kafka broker processes the incoming data stream as topics.

Next, two parallel data stream pipelines are available:
- Python script which acts as Kafka consumer and stores the data into MongoDB. The results are then visible in Grafana.
- ELK stack, where Logstash aggregates data from Kafka topic, processes it and ships to Elasticsearch. Kibana allows exploring and validation of data ingested from Kafka and indexed in Elasticsearch.
  Morover, Kibana provides the ability to create visualizations and dashboards that can help make the analysis more intuitive and interactive.

All elements of above mentioned pipeline are implemented as containers with usage of Docker-Compose.

### This repo includes only code for Siemens PLC (TIA Portal). The IT part is located in separate repository.   
