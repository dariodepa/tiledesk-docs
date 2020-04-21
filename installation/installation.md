# Installation

## Run with Docker <a id="run-with-docker"></a>

Docker is the simplest way to run Tiledesk. There’s a public repository on [Docker Hub](https://hub.docker.com/u/tiledesk).

Please refer to [Running Tiledesk with Docker Compose](running-tiledesk-with-docker-compose.md) .

## Run from Source Code <a id="run-from-sourcecode"></a>

Use this guide if you want to fully customize the product.

Please refer to [Running Tiledesk from Source Code](running-tiledesk-from-sourcecode.md) .


# Choosing hardware

## Server

### Minimum infrastructure

The minimum recommended infrastructure to install Tiledesk is based on two different servers. One server to run Tiledesk Server, Tiledesk Dashboard, Widget and WebChat and another server to run MongoDB.

With minimum infrastructure, you can have the servers up and running, but quality parameters such as performance and availability (also factors such as backups, redundancy, and recovery) are not considered. 

The default instance type will be a t2.small as this is the minimum instance type determined to run Tiledesk Server, but this instance is more indicated for testing environments. A ‘c4.large’ instance is ideal for a production environment.

If you like Heroku, at least the Hobby dyno type is recommended for small apps even if Tiledesk also works with the free level.

## Front-end components

To serve the Tiledesk front-end components (Dashboard, Widget, Web Chat) we suggest to use AWS S3 + CloudFront. Enable gzip compression is a good choice to reduce network traffic and improve performance. See here: https://aws.amazon.com/blogs/aws/new-gzip-compression-support-for-amazon-cloudfront/

## Database

We recommend you run MongoDB on : 
- MongoAtlas. M10 is ok for testing and low traffic application. It supports continuous backup. For high-traffic solution M30 ( or upper) is a good choice.   
- locally in replica set mode, with at least three nodes for availablity. Each node should run in a separate Availability Zone.
