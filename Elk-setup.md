# ELK Stack Setup (SIEM Integration)

## Installation
Installed Elasticsearch, Logstash, and Kibana on Ubuntu server.

## Log Ingestion
Configured Logstash to monitor:
`/var/log/auth.log`

## Detection
Filtered:
"Failed password" events

## Visualization
Access Kibana:
http://<ubuntu-ip>:5601

## Example Attack
- Hydra brute-force attack from Kali
- Logs ingested and visualized in Kibana
