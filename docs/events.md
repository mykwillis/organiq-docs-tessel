# Using Events for Device Notifications

There are many situations in which it is useful for devices to be able to notify external applications of certain events. For example, a connected garage door might notify a security application whenever it is opened or closed, or a leak detector could be wired to an application that will send an email when it detects water on the floor.

It is often prohibitively expensive, in terms of network utilization and battery consumption, for applications to continually poll devices to query for these conditions. Organiq therefore supports remote eventing that allows applications to register their interest in certain device events and be notified when they occur.

## Emitting Events from Devices

Emitting an event from a device in Organiq is done in the same way as emitting a conventional event in JavaScript. Simply call the `emit` method of your device object with the event name and any parameters you want to associate with it:

    var device = { /* your device implementation */ }
    organiq.registerDevice('MyDevice', device);
    // some time later...
    device.emit('somethingHappened', { severity: 'BAD' });

The emitted event will be sent to all currently registered listeners, across the network.

Note: you didn't need to define the `emit` method on your device. When you pass an object to `registerDevice` that does not already define an `emit` method, an instance of EventEmitter is automatically created and wired up for you.

## Getting Notifications of Device Events

When writing client applications, you can be notified of device events by registering a callback function with the device received from `getDevice`:

    organiq.getDevice('MyDevice')
        .then(function(device) {
            device.on('somethingHappened', function(data) {
                if ( data.severity === 'BAD' ) { ... }
            }
        });


