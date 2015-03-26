# Configuration Settings

The Organiq SDK has several configuration settings that affect its runtime
behavior. Configuration settings can be supplied as part of the `options` passed
to the Organiq constructor, as parameters in a configuration file
(organiq.json), or as environment variables.

## Settings via Configuration File (organiq.json)

This file is a JSON formatted file located in the project's root directory. An
example file might look like this:

    {
        "apiRoot": "ws://organiq.example.com:1340",
        "namespace": "."
    }

Where:
* `apiRoot` - connection string for the Organiq server being used.
* `namespace` - the default namespace to use for device identifiers.

## Settings via environment variables

    $ export ORGANIQ_APIROOT='ws://organiq.example.com:1340'
    $ export ORGANIQ_NAMESPACE='.'

## Settings via Organiq constructor

Settings passed via constructor arguments take precedence over any settings in
the environment or supplied in organiq.json.

    ```JavaScript
    var organiq = require('organiq');

    var options = {apiRoot: 'ws://organiq.example.com:1340', namespace = '.'};
    var app = new organiq(options);
    // ...
    ```

# Settings for Development

When developing applications in a local network environment, you will typically
use a development version of the Organiq server running on your development
machine. In order for this server to be found by, e.g., a Tessel, you need
to supply the IP address of this server in `organiq.json`.

The easiest way to create an organiq.json file is to use the CLI's `init'
option from the root of your project directory, like this:

    $ organiq init --local-dev

This will write out a simple organiq.json in the current directory that sets
up `apiRoot` to point at the primary IP address of the local host.

