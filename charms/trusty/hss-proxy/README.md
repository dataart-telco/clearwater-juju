# Overview

This is a proxy [Juju charm](https://jujucharms.com/about) for the 3GPP-Cx interface to the HSS.  Since it is just a proxy, it does not actually provide HSS function - it can just be configured with the location of the HSS, and then terminate the relation with the 3GPP-Cx user.

# Configuration

-  `hss_host`: The host on which the HSS is running.
-  `hss_realm`: The realm to which the HSS belongs.
-  `hss_port`: The port on which the HSS listens.

# Contact and Upstream Project Information

Project Clearwater is an open-source IMS core, developed by [Metaswitch Networks](http://www.metaswitch.com) and released under the [GNU GPLv3](http://www.projectclearwater.org/download/license/). You can find more information about it on [our website](http://www.projectclearwater.org/) or [our documentation site](https://clearwater.readthedocs.org).

Clearwater source code and issue list can be found at https://github.com/Metaswitch/.

If you have problems when using Project Clearwater, read [our troubleshooting documentation](http://clearwater.readthedocs.org/en/latest/Troubleshooting_and_Recovery/index.html) for help, or see [our support page](http://clearwater.readthedocs.org/en/latest/Support/index.html) to find out how to ask mailing list questions or raise issues.
