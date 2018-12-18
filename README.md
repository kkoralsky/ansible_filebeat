Filebeat
========

Ansible role to install filebeat agent forwarding logs to logstash

Requirements
------------

Logstash running in the network configurable by `filebeat_logstash_hosts`.

Role Variables
--------------

- `filebeat_user` - user that will run filebeat daemon and own all files related
  to the role (configuration, logs etc.) (default: ansible provision user)
- `filebeat_home` - main directory where all mentioned files will be stored (filebeat subderictory of home directory of `filebeat_user`)
- `filebeat_name` - name of the filebeat instance
- `filebeat_index` - ES index prefix where all data will be eventually stored 
- `filebeat_document_type` - ES index type
- `filebeat_logstash_hosts` - list of logstash *connection strings* (in the format: `host/ip:port`)
- `filebeat_fields` - mapping annotating each log *beat* (empty)
- `filebeat_inputs` - list of mappings representing inputs with following keys:
    - `document_type`
    - `fields` - mapping annotating given input; this is replacing `filebeat_fields` if defined
    - `paths` - list of paths (supports globs)
    - `multiline`
    - `include_lines`
    - `exclude_lines`
    

Dependencies
------------


Example Playbook
----------------


    - hosts: servers
      roles:
         - { role: filebeat, x: 42 }

License
-------

BSD
