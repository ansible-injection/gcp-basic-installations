Role Name
=========

Basic installations via downloading files onto provisioned compute instance(s) on GCP.

- Extracting
- Chang ownership of user and group

Requirements
------------

Uses standard ssh, so nothing specific to GCP modules!

- _ansible_ client
- _ansible.cfg_ file
- _hosts_ file
- gcp account

Role Variables
--------------

defaults/main.yml
```
installation:
    xxx:                               #username!
      src: "https://ftp.itu.edu.tr/Mirror/Apache/hadoop/common/hadoop-3.2.1/hadoop-3.2.1.tar.gz"
      dest: "/"                        #tool extraction path
```

Dependencies
------------

- gcp_instances: to create instance(s) on GCP
- gcp_basic_configurations: to install some fundamental packages, user creations, mounting/formating disks etc.. on GCP instances

Example Playbook
----------------

[Click](https://github.com/ansible-injection/test-gcp-iaas-roles) to test and see example playbooks.

hosts
```
# static inventory file

# group w/ alias suh as hadoop/bigdata/ ....
# Inspire from network Tags in GCP while host grouping
# Update IPs
# possible params: ansible_host=, ansible_user=, ansible_ssh_pass=, ansible_connection=ssh/winrm/localhost
[web]
standalone-node ansible_host=34.90.161.000
```

ansible.cfg
```
[defaults]
host_key_checking = False
inventory = hosts

remote_user = tansudasli                          #your gcp account
private_key_file = ~/.ssh/google_compute_engine   #If set, always uses this for authentication

[inventory]
# List of enabled inventory plugins and the order in which they are used.
enable_plugins = host_list, script, yaml, ini, auto, gcp_compute

```

configuration.yaml
```
- name: Fundamental Compute Instance Configurations
  hosts: 
    - all
  become: yes
  gather_facts: no
  
  roles:

    - role: tansudasli.gcp_basic_installations
      installation:
        xxx:                                    #username!
          src: "https://ftp.itu.edu.tr/Mirror/Apache/hadoop/common/hadoop-3.2.1/hadoop-3.2.1.tar.gz"
          dest: "/"                             #tool extraction path 
```

License
-------

Apache-2.0

Author Information
------------------

[tansudasli](http://github.com/tansudasli)
