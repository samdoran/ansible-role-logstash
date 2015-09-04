Logstash
========

Setup logstash shipping and parsing nodes. Two groups, `ls_parser` and `ls_shipper` should contain the appropriate hosts. The `ls_shipper` host takes files as input, does minimal processing, then outputs to redis. The `ls_parser` hosts take input from redis, process, then output to an elasticsearch cluster.

Requirements
------------

* Java
* logstash user account
* logreader user group

Role Variables
--------------

| Name                     | Default | Descrription |
|---------------------------|--------|---------------|
| `logstash_open_files`    | 65535    | Set ulimit to this number for logstash process   |
| `redis_host_1`    |  null   |  IP or hostname for first redis server |
| `redis_host_2`    |  null   | IP or hostname for first second server  |
| `logstash_ssl_crt_path`    | /etc/pki/tls/certs    | Path where SSL cert will be copied   |
| `logstash_ssl_key_path`    | /etc/pki/tls/private    | Path where SSL private key will be copied   |
| `logsasth_ssl_crt`    |  null   |  Public SSL cert |
| `logstash_ssl_key`    |  null   |  Private SSL key. I recommend storing this in an Ansible vault |
| `logstash_plugins` | undefined | List of plugins to install |

Dependencies
------------

* redis
* elasticsearch
* kibana

Example Playbook
-------------------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: ls_parser;ls_shipper
      roles:
         - logstash

License
-------

MIT

