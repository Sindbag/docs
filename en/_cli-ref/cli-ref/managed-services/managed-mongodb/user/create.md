---

__system: {"dislikeVariants":["No answer to my question","Recomendations didn't help","The content doesn't match title","Other"]}
---
# yc managed-mongodb user create

Create a MongoDB user.

#### Command Usage

Syntax: 

`yc managed-mongodb user create <USER-NAME> [Flags...] [Global Flags...]`

#### Global Flags

| Flag | Description |
|----|----|
|`--cluster-id`|<b>`string`</b><br/> ID of the MongoDB cluster.|
|`--cluster-name`|<b>`string`</b><br/> Name of the MongoDB cluster.|
|`--async`| Display information about the operation in progress, without waiting for the operation to complete.|
|`--password`|<b>`string`</b><br/> Password of the MongoDB user. --permission PROPERTY=VALUE[,PROPERTY=VALUE...] Database and role in the database to assign to the user. Can be specified multiple times.  Possible property names:  database Name of the database that the permission grants access to.  role Role in the database to assign to the user. Can be specified multiple times.|

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