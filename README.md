Software versions.
1. Juju 2.0-beta12-xenial-amd64
2. Ubuntu Precise 12.04.5 image for instances( i was tried 12.04.4, but in my case juju can't raise up instances. Juju agent can't fetch tools from controller node due to error: "curl: (35) error:1407742E:SSL routines:SSL23_GET_SERVER_HELLO:tlsv1 alert protocol version" . Such behavior has led to the eternal "pending" status of juju workagent )

You can use tar.gz archive or try to deploy it from scratch

From Archive
1. wget https://www.dropbox.com/s/mndr2nq5axtykqp/clearwater-juju.tar.gz
2. tar -xzvf clearwater-juju.tar.gz
3. cd ./clearwater-juju/charms/bundles/clearwater/bundle/
4. juju deploy ./local_bundle.yaml

From scratch.
1. You should use Release-100 tag of CW IMS from here https://github.com/Metaswitch/clearwater-juju/
   May be useful -> http://julienrenaux.fr/2013/10/04/how-to-automatically-checkout-the-latest-tag-of-a-git-repository/
   or simply execute :
   git checkout Release-100
2. Rewrite bundle.yaml to make it executable by juju deploy command because it seems that juju 2.0 could work only with local paths like this "charm: ../../../precise/clearwater-sprout"
   Use local precise version for CW charms and cs:~lazypower/precise/dns-3 for DNS
3. When all CW nodes will be deployed and DNS charm failed with "hook failure: install"
   In separate tmux window execute "juju debug-hooks <dns_unit_name>"
   In other tmux window type "juju resolved --retry <dns_unit_name>"
   Return to debug window and do next:
   		sudo apt-get install python-dns
   		sudo apt-get install python-jinja2
   		rm -rf /etc/bind/zone-backup
   		cd ./hooks
   		./install
   Then you should execute called hooks by hands or if they don't exist just type "exit". After you finish this process all should works fine.
