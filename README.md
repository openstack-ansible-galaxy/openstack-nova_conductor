Nova conductor
=========

OpenStack Nova conductor service installation

_Tested on Ubuntu Precise (12.04) and Trusty (14.04)_

Requirements
------------

A MySQL server. See `mysql_hostname`, `mysql_admin_username` and
`mysql_rootpass` below.

A RabbitMQ server. See `rabbit_hostname`, `rabbit_username` and
`rabbit_pass` below.

Role Variables
--------------

# Other systems/services
* `rabbit_hostname`:  Hostname/IP address where the RabbitMQ service runs.
                      Defaults to "localhost".
* `rabbit_username`:  RabbitMQ username for nova conductor.
                      It must already exist.
                      Defaults to "rabbit\_username\_default".
* `rabbit_pass`:      RabbitMQ password for nova conductor.
                      Defaults to "rabbit\_pass\_default".

* `mysql_hostname`:       MySQL server address. Defaults to "localhost".
* `mysql_admin_username`: MySQL admin username. Defaults to "root".
* `mysql_rootpass`:       MySQL admin password. Defaults to "mysql\_root\_default".

# Role specific
* `nova_conductor_hostname`:
                      Hostname/IP address where this role runs.
                      It will be used to set keystone endpoints.
                      Defaults to first interface IP address (eth0).

* `nova_conductor_dbpass`:
                      Desired nova conductor user password for the nova
                      database. Defaults to "nova\_conductor\_dbpass\_default".

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: conductor001
      roles:
        - role: nova_conductor
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
