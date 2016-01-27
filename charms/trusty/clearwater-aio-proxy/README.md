# Overview

This is a [Juju charm](https://jujucharms.com/about), which allows configuration of the [Project Clearwater](http://projectclearwater.org) IMS core's [all-in-one](http://clearwater.readthedocs.org/en/stable/All_in_one_Images/index.html) node.

This is a proxy charm, meaning that you must spin up the all-in-one VM first, and then point this charm at it to manage it.

Since the all-in-one node does not support scaling up, neither does this charm.

# Deployment

## Initial deployment

The all-in-one VM image should be downloaded from [http://vm-images.cw-ngv.com/cw-aio.ova](http://vm-images.cw-ngv.com/cw-aio.ova) and deployed onto your virtualization platform.

The proxy charm should then be deployed, pointing at the all-in-one VM.

# Using the All-in-One Node

Once installed, the all-in-one node will listen for SIP traffic on port 5060 (both TCP and UDP).  You can use a standard SIP client (e.g. Blink, Boghe or X-Lite) to register against Bono's public IP (which you can find with `juju status clearwater-bono`) and make calls.

Our ["Making your first call" documentation](http://clearwater.readthedocs.org/en/latest/Making_your_first_call/index.html) has more information on this process.

# Configuration

-  `proxied_ip`: The IP address of the All-in-One node to manage
-  `home_domain`: The home domain for this service
-  `base_number`: The first number to be allocated in the number range
-  `number_count`: The count of numbers to allocate

# Actions

This proxy charm exposes two actions.

-  `create-user`: Creates a user
    -  `number`: The first number to provision
    -  `password`: The first number's password

-  `delete-user`: Deletes a user
    -  `number`: The number to delete

For example, `juju action do clearwater-aio-proxy/0 create-user number=\"1234567890\" password=secret` creates a user.  (Note that the escaped double-quotes are required to avoid juju parsing the number as an integer rather than a string.)

# Contact and Upstream Project Information

Project Clearwater is an open-source IMS core, developed by [Metaswitch Networks](http://www.metaswitch.com) and released under the [GNU GPLv3](http://www.projectclearwater.org/download/license/). You can find more information about it on [our website](http://www.projectclearwater.org/) or [our documentation site](https://clearwater.readthedocs.org).

Clearwater source code and issue list can be found at https://github.com/Metaswitch/. Bono's source code can be found at https://github.com/Metaswitch/sprout/.

If you have problems when using Project Clearwater, read [our troubleshooting documentation](http://clearwater.readthedocs.org/en/latest/Troubleshooting_and_Recovery/index.html) for help, or see [our support page](http://clearwater.readthedocs.org/en/latest/Support/index.html) to find out how to ask mailing list questions or raise issues.
