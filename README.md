Nova conductor
=========

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
| `my_ip` | `{{ ansible_eth0.ipv4.address }}` | Management IP for nova-conductor |
| `nova_conductor_hostname` | `localhost` | Hostname/IP address where this role runs ||
| `nova_conductor_dbpass` | `nova_pass_default` |  Desired nova conductor user password for the nova database ||

### MySQL (must exist)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `mysql_admin_username` | `root` | MySQL admin username ||
| `mysql_hostname` | `localhost` | MySQL server address ||
| `mysql_rootpass` | `mysql_root_default` | MySQL admin password ||


### RabbitMQ (must exist)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `rabbit_hostname` | `localhost` | Hostname/IP address where the RabbitMQ service runs ||
| `rabbit_username` | `rabbit_username_default` | RabbitMQ username for glance ||
| `rabbit_pass` | `rabbit_pass_default` | RabbitMQ password for glance. ||


Dependencies
------------

None.

Example Playbook
----------------

    - hosts: conductor001
      roles:
        - role: openstack-nova_conductor
          mysql_rootpass: "{{ MYSQL_ROOT }}"
          rabbit_username: "openstack-nova"
          rabbit_pass: "{{ RABBIT_NOVA_PASS }}"
          nova_conductor_dbpass: "{{ NOVA_DBPASS }}"

License
-------

Apache

Author Information
------------------

Davide Guerri - davide.guerri@gmail.com
