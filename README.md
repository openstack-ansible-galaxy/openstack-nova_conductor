Nova conductor
=========

**Status**
* [![Build Status](https://travis-ci.org/openstack-ansible-galaxy/openstack-nova_conductor.svg?branch=master)](https://travis-ci.org/openstack-ansible-galaxy/openstack-nova_conductor) on master branch
* [![Build Status](https://travis-ci.org/openstack-ansible-galaxy/openstack-nova_conductor.svg?branch=development)](https://travis-ci.org/openstack-ansible-galaxy/openstack-nova_conductor) on development branch
* [![Ansible Galaxy](http://img.shields.io/badge/dguerri-openstack--nova_conductor-blue.svg)](https://galaxy.ansible.com/list#/roles/1772) on Ansible Galaxy

OpenStack Nova conductor service installation

_Tested on Ubuntu Precise (12.04) and Trusty (14.04)_

Requirements
------------

A MySQL server. See below.

A RabbitMQ server. See below.

Role Variables
--------------
### Nova conductor (set by this role)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `nova_conductor_database_url` | `sqlite:////var/lib/nova/nova.sqlite` | Database URI ||
| `my_ip` | `{{ ansible_eth0.ipv4.address }}` | Management IP for nova-conductor |
| `rabbit_hostname` | `localhost` | Hostname/IP address where the RabbitMQ service runs ||
| `rabbit_username` | `rabbit_username_default` | RabbitMQ username for Nova conductor ||
| `rabbit_pass` | `rabbit_pass_default` | RabbitMQ password for Nova conductor. ||


Dependencies
------------

None.

Example Playbook
----------------

    - hosts: conductor001
      roles:
        - role: openstack-nova_conductor
          rabbit_username: "openstack-nova"
          rabbit_pass: "{{ RABBIT_NOVA_PASS }}"

---

A complete Ansible playbook demo, which uses this role, is available on Github (openstack-ansible-galaxy/vagrant-ansible-openstack) <https://github.com/openstack-ansible-galaxy/vagrant-ansible-openstack>

---


License
-------

Apache

Author Information
------------------

Davide Guerri - davide.guerri@gmail.com
