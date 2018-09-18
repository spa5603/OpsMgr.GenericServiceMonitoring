# OpsMgr GenericServiceMonitoring ManagementPack

## Introduction:
It is often necessary to monitor windows services across your entire SCOM environment. This ManagementPack processes the services, provided by CSV and detects them into their own class. Service wildcard is also possible.

## Configuration:
##### CSV File Layout:

**ServiceA;HostA,HostB;none**

ServiceA is monitored for HostA and HostB. There is no exclusion.

**ServiceB;*;none**

ServiceB is monitored on every Host. There is no exclusion.

__Service*;*;HostB__

Service*(wildcard) is monitored on every Host and excluded for HostB.

##### Start Sevice Ingest Task

##### Check discoverd Services

## Examples:

## Views:

##### State View Discoverd Services:
![alt text](https://github.com/spa5603/OpsMgr.GenericServiceMonitoring/blob/master/Graphics/StateView%20-%20Discovered%20Services.jpg)

##### State View Management Server
![alt text](https://github.com/spa5603/OpsMgr.GenericServiceMonitoring/blob/master/Graphics/StateView%20-%20Management%20Server.jpg)
