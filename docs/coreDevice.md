# Core device

[This documentation refers to unofficial internal functionality that may change or disappear at any time.]

Every Organiq node has a virtual device named ***:core*** that exposes information about the devices registered on that node, and the clients connected to it. It is intended primarily for system administration and troubleshooting.

You can obtain a reference to the core device for a node by calling getDevice(':core') from within the node. Because the device exists in the non-routable NULL namespace, it is not, in general, possible to obtain a direct reference to the core device of another node.

One exception to that is organiq gateway servers, which expose device-manipulation methods via HTTP methods. These methods can be used to inspect the core device on that gateway.

For example,

    http://organiq.example.com:1340/dapi/:core/ConnectedDevices

Will use the HTTP device API interface to return a JSON-formatted list of devices on the node at organiq.example.com:1340.

## Methods

### ConnectedDevices

Returns information about all devices connected on the local node. Information is returned as a list of devices, each of which has the following properties:
# deviceid
# domain
# isLocal

Example request:
    http://organiq.example.com:1340/dapi/:core/ConnectedDevices
    
Example response:
    [{"deviceid":":core","domain":"","isLocal":true},
     {"deviceid":".:mocktesseldevice","domain":".","isLocal":true}]

## Properties

None.

## Events

None.

