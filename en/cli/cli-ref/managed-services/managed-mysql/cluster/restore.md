---

__system: {"dislikeVariants":["No answer to my question","Recomendations didn't help","The content doesn't match title","Other"]}
---
# yc managed-mysql cluster restore

Restore MySQL cluster

#### Command Usage

Syntax: 

`yc managed-mysql cluster restore [Flags...] [Global Flags...]`

#### Global Flags

| Flag | Description |
|----|----|
|`--backup-id`|<b>`string`</b><br/> ID of the backup to create a cluster from.|
|`--time`|<b>`timestamp`</b><br/> Timestamp in RFC3339 of the moment to which the MySQL cluster should be restored.|
|`--name`|<b>`string`</b><br/> Cluster name.|
|`--description`|<b>`string`</b><br/> Cluster description.|
|`--environment`|<b>`string`</b><br/> Cluster environment. Values: production, prestable.|
|`--network-id`|<b>`string`</b><br/> Network id.|
|`--network-name`|<b>`string`</b><br/> Network name. --host PROPERTY=VALUE[,PROPERTY=VALUE...] Individual configurations for hosts that should be created for the MySQL cluster.  Possible property names:  zone-id ID of the availability zone where the host resides.  subnet-id ID of the subnet that the host should be created in.  subnet-name Name of the subnet that the host should be created in.  assign-public-ip Whether the host should get a public IP address on creation.  |
|`--datalens-access`| Allow access for DataLens|
|`--websql-access`| Allow access for Web SQL|
|`--mysql-version`|<b>`string`</b><br/> Version of MYSQL used in the cluster. Values: 8.0, 5.7|
|`--resource-preset`|<b>`string`</b><br/> ID of the preset for computational resources available to a host (CPU, memory etc.).|
|`--disk-size`|<b>`byteSize`</b><br/> Volume of the storage available to a host.|
|`--disk-type`|<b>`string`</b><br/> Type of the storage environment for the host.|
|`--backup-window-start`|<b>`timeofday`</b><br/> Start time for the daily backup in UTC timezone. Format: HH:MM:SS --labels key=value[,key=value...] A list of label KEY=VALUE pairs to add. --security-group-ids value[,value] A list of security groups for the MySQL cluster.|
|`--async`| Display information about the operation in progress, without waiting for the operation to complete.|

#### Flags

| Flag | Description |
|----|----|
|`--profile`|<b>`string`</b><br/>Set the custom configuration file.|
|`--debug`|Debug logging.|
|`--debug-grpc`|Debug gRPC logging. Very verbose, used for debugging connection problems.|
|`--no-user-output`|Disable printing user intended output to stderr.|
|`--retry`|<b>`int`</b><br/>Enable gRPC retries. By default, retries are enabled with maximum 5 attempts. Pass 0 to disable retries. Pass any negative value for infinite retries. Even infinite retries are capped with 2 minutes timeout.|
|`--cloud-id`|<b>`string`</b><br/>Set the ID of the cloud to use.|
|`--folder-id`|<b>`string`</b><br/>Set the ID of the folder to use.|
|`--folder-name`|<b>`string`</b><br/>Set the name of the folder to use (will be resolved to id).|
|`--token`|<b>`string`</b><br/>Set the OAuth token to use.|
|`--format`|<b>`string`</b><br/>Set the output format: text (default), yaml, json, json-rest.|
|`-h`,`--help`|Display help for the command.|