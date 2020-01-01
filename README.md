# Graylog-SpringBoot
Server logs management platform


Introduction
Graylog is a powerful open-source log management platform. It aggregates and extracts important data from server logs, which are often sent using the Syslog protocol. It also allows you to search and visualize the logs in a web interface.


INTRODUCTION

Graylog System comprises of :

    1. Graylog server
    2. MongoDB
    3. Elasticsearch

Simple System Configuration 
Graylog and elasticsearch resides on different hosts whereas mongodb and graylog can be on same host . MongoDB stores application configuration information and hence load on mongoDB is low . Data goes into elasticsearch .



DESIGN FEATURES

Graylog uses index set which is an abstraction of elasticsearch indices .
Maintains index aliases per index set which points to current write-active index.
There is always one index to which messages are written until the rotation criteria has met 
Rotation criteria is a strategy to determine when to rotate currently active write index.
Rotation criteria includes number of documents , index size and index time.
Graylog uses retention strategy to cleanup old indices which includes deleting index.(Here we give a count i.e maximum number of indices to keep before deleting 

Graylog is writing messages sequentially into ES . It keep information about time range each index covers . It selects list of indices to query when having a time range provided. If no time range is provided it will search into all the indices .

REQUISITES FOR SETUP

Please find DOC enclosed for setting up graylog machine and spring boot application with necessary configuration to communicate with graylog server.
