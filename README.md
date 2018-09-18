# OpsMgr GenericServiceMonitoring ManagementPack

## Introduction:
It is often necessary to monitor windows services across your entire SCOM environment. This ManagementPack processes the services, provided by CSV and detects them into their own class. Service wildcard is also possible.

## Configuration:
##### CSV File Layout
ServiceName;HostA,HostB;none

ServiceName;*;none

Service*;*;HostB

##### Start Sevice Ingest Task

##### Check discoverd Services

## Examples:

## Views:

##### State View Discoverd Services:
![alt text](https://github.com/spa5603/OpsMgr.GenericServiceMonitoring/blob/master/Graphics/StateView%20-%20Discovered%20Services.jpg)

##### State View Management Server
![alt text](https://github.com/spa5603/OpsMgr.GenericServiceMonitoring/blob/master/Graphics/StateView%20-%20Management%20Server.jpg)
