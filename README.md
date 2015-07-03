# Overview

This repository contains a collection of [Juju charms and deployment bundles](https://jujucharms.com/about), which support deployment and scaling of a [Project Clearwater](http://www.projectclearwater.org) IMS core.

# Usage

Before deploying this charm, you should have bootstrapped a Juju environment, as documented at https://jujucharms.com/docs/stable/getting-started. This charm has been tested on Amazon EC2, with plans to test on OpenStack in the near future - if you get it working on a different cloud service, please let us know!

Clearwater is a reasonably complex system (especially compared to typical beginner Juju examples like Wordpress + MySQL) - deploying a Clearwater IMS core involves deploying and configuring six or seven charms and adding relations between them.

Fortunately, we've set up a Juju bundle that ties all these charms and their relations together, allowing a full system to be deployed in a single step. The bundle contains some default configuration, but additional configuration files can be used to customise the deployment - see [bundle-config.yaml.example](bundle-config.yaml.example) for an example.

A Clearwater system can be deployed in a Juju environment by creating a bundle-config.yaml file then running the following commands.

    git clone -b dnsaas https://github.com/Metaswitch/clearwater-juju.git
    cd clearwater-juju
    JUJU_REPOSITORY=charms juju-deployer -c charms/bundles/clearwater/bundle/bundles.yaml -c bundle-config.yaml

# Configuration

See [bundle-config.yaml.example](bundle-config.yaml.example), which lists the main configuration fields with comments about their meanings.

# Testing

This repository contains Amulet tests for automated testing. To run them, use:

    git clone -b dnsaas https://github.com/Metaswitch/clearwater-juju.git
    cd clearwater-juju
    JUJU_REPOSITORY=charms juju test -o logs -v -p JUJU_REPOSITORY,HOME --timeout=1200s

# Contact and Upstream Project Information

Project Clearwater is an open-source IMS core, developed by [Metaswitch Networks](http://www.metaswitch.com) and released under the [GNU GPLv3](http://www.projectclearwater.org/download/license/). You can find more information about it on [our website](http://www.projectclearwater.org/) or [our documentation site](https://clearwater.readthedocs.org).

Clearwater source code and issue trackers can be found at https://github.com/Metaswitch/.

If you have problems when using Project Clearwater, read [our troubleshooting documentation](http://clearwater.readthedocs.org/en/latest/Troubleshooting_and_Recovery/index.html) for help, or see [our support page](http://clearwater.readthedocs.org/en/latest/Support/index.html) to find out how to ask mailing list questions or raise issues.
