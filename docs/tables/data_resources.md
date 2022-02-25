
<style>
  .md-content__button {
    display: none;
  }
</style>

**This information is also available in** **[list format](/attributes/data_resources/)**

| Concept        | Key                        | Subkey   | Type                              | Example Value                 | Comment                                                                                                                                                                                                                                  | Condition   |
|:---------------|:---------------------------|:---------|:----------------------------------|:------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------|
| Data Resources |                            |          |                                   |                               |                                                                                                                                                                                                                                          |             |
|                | DATA_RESOURCE_ID           |          | String                            | file1                         | human-readable identifier, unique within a Microservice                                                                                                                                                                                  | mandatory   |
|                | DATA_KIND                  |          | List( DATA_KIND)                  | {FILE, STREAM}                | supported types of the data resource (e.g. file/object storage, database management system, streaming broker). FILE can mean a single file or a folder.                                                                                  | mandatory   |
|                | DATA_DIRECTION             |          | List( DATA_DIRECTION)             | {SOURCE, SINK, BIDIRECTIONAL} | supported direction of data flow (source: data provider, sink: data consumer/storage)                                                                                                                                                    | mandatory   |
|                | DATA_FORMAT                |          | List( DATA_FORMAT)                | {application/zip, image/jpg}  | supported format/encoding of the data produced or consumed by the data resource as a MIME type (IETF RFC 6838 https://www.sitepoint.com/mime-types-complete-list/). More than one can appear here (remote directory with several files). | optional    |
|                | DATA_SOURCE_TYPE           |          | List( DATA_SOURCE_TYPE)           | {MYSQL, KAFKA}                | supported exact type of the data resource. Typically corresponds to the scheme part (protocol://) of DATA_URI                                                                                                                            | optional    |
|                | DATA_PROTOCOL              |          | List( DATA_PROTOCOL)              | {HTTP}                        | supported protocols                                                                                                                                                                                                                      | optional    |
|                | DATA_AUTH_TYPE             |          | List( DATA_AUTH_TYPE)             | {tls_mutual, userpass}        | supported authentication type                                                                                                                                                                                                            | optional    |
|                | DATA_MYSQL_DIALECT         |          | List( DATA_MYSQL_DIALECT)         | {mariadbdialect}              | supported MYSQL dialect                                                                                                                                                                                                                  | optional    |
|                | DATA_MQTT_PROTOCOL_VERSION |          | List( DATA_MQTT_PROTOCOL_VERSION) | {2.3.1}                       | supported MQTT protocol version                                                                                                                                                                                                          | optional    |
|                | DATA_KAFKA_BROKER_VERSION  |          | List( DATA_KAFKA_BROKER_VERSION)  | {2.7.1, 2.5}                  | supported Kafka broker version                                                                                                                                                                                                           | optional    |
|                | DATA_S3_REGION             |          | List( DATA_S3_REGION)             | {eu-central-1}                | supported S3 region                                                                                                                                                                                                                      | optional    |
|                | DATA_SCHEMA                |          | List( DATA_SCHEMA)                | {jpg}                         | supported internal message structure, semantics, ontology. It can be any file (doc, rdf, owl, etc.). Asset Administration Shell, IEC 61360 - Common Data Dictionary, …                                                                   | optional    |