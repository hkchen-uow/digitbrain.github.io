# Deployments in DIGITbrain

## Introduction

A deployment in DIGITbrain specifies the infrastructure that a desired DMA
Tuple will be deployed across.

## Metadata describing Deployment

The [metadata specification](assets/deployment.md) for a DIGITbrain Deployment
has three sections:

- [Description](#description)
- [Deployments](#deployments)
- [Data Source Mapping](#data-source-mapping)

### Description

This section provides high-level descriptive metadata for the deployment being defined.

`name`

:   **Required**– A memorable name for this deployment.

`author`

:   **Required**– The author of this deployment metadata.

`date`

:   **Auto-generated**– Today's date.

`id`

:   **Auto-generated**– A DIGITbrain ID.

### Deployments

Here it is necessary to provide details on the type of infrastructure that this deployment
will define, along with all the configuration details of that infrastructure.

The following fields are available:

`type`

:   **Required**– DIGITbrain supports cloud infrastructure deployed via the
CloudBroker platform, or bring-your-own Linux-based Edge devices. This should
be specified in this field. The other metadata in this section should be
completed according to the type (e.g. CloudBroker-specific metadata is not required
if `type: edge`)

    === "cloudbroker"

        ``` yaml
        type: cloudbroker
        cloudbroker:
          deployment_id:
          instance_type_id:
          key_pair_id:
          opened_port:
          endpoint:
        ```

    === "edge"

        ``` yaml
        type: edge
        edge:
          endpoint:
        ```

`cloudbroker.deployment_id`

:   **Required**– A CloudBroker deployment ties together software,
resource and region. Indicative IDs are given below, but any LTS
Debian-based Linux distribution should be supported. It is recommended
to use the MiCADO-Optimised deployment.


    === "MiCADO-Optimised"

        ``` yaml
        cloudbroker:
          deployment_id: 27f3dd48-1dac-4d3c-8b7f-39338ed55543
        ```

    === "Ubuntu 20.04"

        ``` yaml
        cloudbroker:
          deployment_id: 16b1e2d4-3a2c-406e-8c45-5637099021f0
        ```

    === "Ubuntu 18.04"

        ``` yaml
        cloudbroker:
          deployment_id: 5a081b54-8992-4ff7-8a21-74e425062507
        ```

    === "Custom"
        ``` html
        <!-- Find your deployment_id at this URL  -->
        https://<cloudbroker-endpoint>/deployments/<deployment-id>
        ```

`cloudbroker.instance_type_id`

:   **Required**– The CloudBroker instance type defines the CPU and RAM
that will be available on the infrastructure. Indicative IDs are given
below. The minimum requirements are a 2 vCPU/2GB RAM

    === "2 vCPU | 4GB RAM"

        ``` yaml
        cloudbroker:
          instance_type_id: ca727925-a5ca-4697-b2c3-8788d82457d5
        ```

    === "4 vCPU | 8GB RAM"

        ``` yaml
        cloudbroker:
          instance_type_id: ffb42759-fb52-4401-9c75-889ea0ed9602
        ```

    === "8 vCPU | 16GB RAM"

        ``` yaml
        cloudbroker:
          instance_type_id: 664330f3-42b1-4f52-a675-fd182a21ef51
        ```

    === "Custom"
        ``` html
        <!-- Find your instance_type_id at this URL  -->
        https://<cloudbroker-endpoint>/instance_types/<instance-type-id>
        ```

`cloudbroker.key_pair_id`

:   **Optional**– The CloudBroker ID for an SSH key pair, for remote
access to the infrastructure. A key pair must be created on the platform.

    === "Custom"
        ``` html
        <!-- Find your key_pair_id at this URL  -->
        https://<cloudbroker-endpoint>/key_pairs/<key-pair-id>
        ```

`cloudbroker.opened_port`

:   **Optional**– A comma-separated string listing port numbers,
which will be opened on the instance (both TCP and UDP protocols
will be affected).

    === "Custom"
        ``` yaml     
        cloudbroker:
          opened_port: 80,443,8080,30010
        ```

`cloudbroker.endpoint`

:   **Required**– The endpoint of the CloudBroker platform that will
handle the deployment of the above infrastructure.

    === "DIGITbrain"
        ``` yaml     
        cloudbroker:
          endpoint: https://cloudsme-cbp.scaletools.com.ua
        ```

`edge.endpoint`

:   **Required**– The endpoint of the bring-your-own Edge device that
provides this Deployment.

    === "Your Edge Device"
        ``` yaml     
        edge:
          endpoint: https://192.168.1.1
        ```

### Data Source Mapping

This section of the metadata maps Microservices to Data assets.

`data_source_mapping`

:   **Required**– Map Microservices (by their ID) to the Data assets
required by each Microservice.

    === "Example"
        ``` yaml     
        data_source_mapping:
          <microservice-A-id>: [<data-A-id>, <data-B-id>]
          <microservice-B-id>: [<data-A-id>]
        ```