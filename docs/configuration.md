# Configuration File (organiq.json)

The `organiq.json` file is used to provide configuration settings to the Organiq
SDK, whether it is used on a device or or a client application. This file is a
JSON formatted file that currently has only a single supported property:

* apiRoot - the URL to the Organiq server

## Local Development

When developing applications in a local network environment, you will typically
use a development version of the Organiq server running on your development
machine. In order for this server to be found by, e.g., a Tessel, you need
to supply the IP address of this server in `organiq.json`.

The easiest way to create an organiq.json file is to use the CLI's `init'
option, like this:

    $ organiq init --local-dev

This will write out a simple organiq.json in the current directory that sets
up `apiRoot` to point at the primary IP address of the local host.

