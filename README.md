Logstash
========
[![Galaxy](https://img.shields.io/badge/galaxy-samdoran.logstash-blue.svg?style=flat)](https://galaxy.ansible.com/samdoran/logstash)
[![Build Status](https://travis-ci.org/samdoran/ansible-role-logstash.svg?branch=master)](https://travis-ci.org/samdoran/ansible-role-logstash)

Setup logstash shipping and parsing nodes. Two groups, `ls_parser` and `ls_shipper` should contain the appropriate hosts. The `ls_shipper` host takes files as input, does minimal processing, then outputs to `redis`. The `ls_parser` hosts take input from redis, process, then output to an elasticsearch cluster.

Requirements
------------

* Java
* `redis` target
* `elasticsearch` hosts

Role Variables
--------------

| Name                     | Default | Descrription |
|---------------------------|--------|---------------|
| `logstash_open_files`    | 65535    | Set ulimit to this number for logstash process   |
| `logstash_version` | `2.4` | Version of Logstash to install. Used to setup up the repository. |
| `redis_group_name`    |  'redis'   | Name of inventory group that contains redis host(s) |
| `logstash_ssl_crt_path`    | /etc/pki/tls/certs    | Path where SSL cert will be copied   |
| `logstash_ssl_key_path`    | /etc/pki/tls/private    | Path where SSL private key will be copied   |
| `logsasth_ssl_crt`    |  null   |  Public SSL cert |
| `logstash_ssl_key`    |  null   |  Private SSL key. I recommend storing this in an Ansible vault |
| `logstash_plugins` | undefined | List of plugins to install |

Dependencies
------------

* redis
* elasticsearch

Example Playbook
-------------------------

    - hosts: ls_parser:ls_shipper
      roles:
         - logstash

License
-------

MIT

