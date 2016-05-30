# spacewalk-ansible-import #

Script for importing a Spacewalk Systemgroup in Ansible hosts file format via Frontier::Client
This software in "works for me" status, tested on Fedora 23 and Centos 7 against Spacewalk 2.4
Use at your own risk!

Pulls the hostlist from Spacewalk API and saves in a file <systemgroup>.hosts for furter usage in Ansible
Config file support (command line options beat config file).

The <systemgroup>.hosts file(s) that you create with this script, you can simply link the /etc/ansible/hosts to it or do deploy your own script here to implement more complex stuff.

# Install: #

cp usr/bin/spacewalk-ansible-import /usr/local/bin/.

mkdir  /etc/spacewalk-ansible-import

cp etc/spacewalk-ansible-import/config /etc/spacewalk-ansible-import/.

cp etc/cron.hourly/97spacewalk-ansible-import.cron /etc/cron.hourly/97spacewalk-ansible-import.cron

vi /etc/spacewalk-ansible-import/config

vi /etc/cron.hourly/97spacewalk-ansible-import.cron

cd /etc/ansible

ln -s hosts <systemgroup>.hosts

# Usage: #

spacewalk-ansible-import *[--spacewalk_server FQDN] [--spacewalk_user USER] [--systemgroup GROUP] [--resource_path PATH] [--spacewalk_password PASS]*

# Shortcomings:#
* Frontier::client connects via plain HTTP
* no help (besides this)
* no manpage


# Todo #

* lock file support for proper cron.hourly execution
