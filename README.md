# Coralogix Azure serverless integration deployment container
Deployment framework for Azure Integrations for the Coralogix platform

Coralogix provides a seamless integration with ``Azure`` cloud so you can send your logs from anywhere and parse them according to your needs.

## Prerequisites

* An Azure account with an active subscription

* Docker

## Installation

Clone this repo:

```bash
$ git clone https://github.com/MichaelBriggs-Coralogix/coralogix-azure-deploy.git
$ cd coralogix-azure-deploy
```

Modify the requisite .vars file for your intended integration deployment:

```bash
BlobStorage.var
StorageQueue.var
EventHub.var
```

Build the docker container:

```bash
$ docker build -t azure-deploy .

# If you're using an ARM CPU, such as an M1 Mac, you'll need to use buildx:
$ docker buildx build --platform linux/amd64 -t azure-int-dep
```

Once the image is built, run it and pass in your integration variables file:

```bash
$ docker run -it --rm --platform linux/amd64 --env-file <integration>.var azure-int-dep
```

The Azure CLI will request authorization. You'll need to follow the prompt and authenticate through your browser with a provided code.