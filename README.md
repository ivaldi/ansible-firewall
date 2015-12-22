Ansible role to configure firewall rules
========================================

Use this role to configure `pf` on OpenBSD or `iptables` on Debian derived distributions. Only simple incoming rules are currently supported. The configuration defaults to denying all incoming connections.

Requirements
------------

This role will work on OpenBSD and Debian derived systems.

Role Variables
--------------

Fill `firewall_rules` with an array of hashes to configure incoming rules. The hash supports the following variables:

 - `allow` whether this is an allow or deny rule, can be either true or false
 - `proto` will default to `tcp` but can also be `udp` or `icmp` for example
 - `source` list of source ip addresses that are allowed/denied
 - `port` the destination port on the server

Dependencies
------------

None.

Example Playbook
----------------

The following playbook will allow all icmp traffic and will allow ssh access from 192.168.0.10.

    - hosts: servers
      vars:
        firewall_rules:
          - proto: icmp
          - port: 22
            source:
              - 192.168.0.10
      roles:
         - ivaldi.firewall

License
-------

BSD

Author Information
------------------

Developed by Frank Groeneveld for use by [Ivaldi](http://ivaldi.nl/).
