# wordpress_centos7_slotted
Ansible scripts to create and install multiple websites, mixture of static and Wordpress-based, on a Centos 7 server.

- Requires Ansible 2.4 or newer
- Requires Python 2.7.10 (on 2.x line) or newer
- Expects CentOS 7 hosts

This playbook installs latest stable (as of 3/24/2018) versions of AMP on top of CentOS 7:
- Apache 2.4
- MySQL 5.7
- PHP 7.2

## Overview

This Ansible script set is a little different in that it considers hosts "VirtualHosts" in the Apache sense of the
word.  So when targeted full domain hosts are targeted by the "all" (hosts) clause in main.yml, each target is
a full domain name like test.fraleys.org and fraleys.org and wilson82.com which all may resolve to the same
underlying IP address or server.  Thus each install target for creating a new website on the server or installing
Wordpress in a website on a server is targeting a full domain name associated with a VirtualHost on the target
server.

A special Ansible group named "base_servers" consists of one full domain name (usually a root domain for the server)
and identifies the underlying hosts or VMs that are targeted.  Install of LAMP components and server-level config
is done against targets in this "base_servers" group.
