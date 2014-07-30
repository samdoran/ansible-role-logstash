Role Name
========

Setup logstash shipping and parsing nodes. Two groups, `ls_parser` and `ls_shipper` should contain the appropriate hosts. The `ls_shipper` host takes files as input, does minimal processing, then outputs to redis. The `ls_parser` hosts take input from redis, process, then output to an elasticsearch cluster.

Requirements
------------

* Java
* logstash user account
* logreader user group

Role Variables
--------------

**logstash_open_files** Set ulimit to this number for logstash process (Default: 65535)

**redis_host_1** IP or hostname for first redis server

**redis_host_2** IP or hostname for first second server

**logstash_ssl_crt_path** Path where SSL cert will be copied (Default: /etc/pki/tls/certs)

**logstash_ssl_key_path** Path where SSL private key will be copied (Default: /etc/pki/tls/private)

**logsasth_ssl_crt** Public SSL cert

**logstash_ssl_key** Private SSL key. I recommend encrypting this using `ansible-vault`


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

