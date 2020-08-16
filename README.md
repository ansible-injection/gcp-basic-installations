Role Name
=========

Basic installations via downloading files onto provisioned compute instance(s) on GCP.

- Extracting
- Changing ownership
- Configuration via files
- Starting

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

- gcp_instances: to create instance(s) on GCP
- gcp_basic_configurations: to install some fundamental packages, user creations, mounting/formating disks etc.. on GCP instances

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

Apache-2.0

Author Information
------------------

[tansudasli](http://github.com/tansudasli)
