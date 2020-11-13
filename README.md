playbook-baseinstall
=========
Ansible playbook to setup MySQL Cluster

Important Variables
------------

Need dataset to define cluster like the following:
```
$ more group_vars/mysql_cluster/*
::::::::::::::
group_vars/mysql_cluster/general.yml
::::::::::::::
role_app_mysql_clusters:
  - name: democluster
    type: master-slave
    hosts:
      - name: master8
        listen_address: 10.128.9.177
        role: master
        repo: distro_default
        version: distro_default
      - name: slave10
        listen_address: 10.128.11.186
        role: slave
        repo: community
        version: "8.0"
::::::::::::::
group_vars/mysql_cluster/vault_vars.yml
::::::::::::::
vault_role_app_mysql_passwd:
  - name: democluster
    hosts:
      - name: master8
        db_root_pw: Secret-234
        users:
          - name: mel
            pw: melpw123
      - name: slave10
        db_root_pw: Secret-345
        slave_repl_user: replication
        slave_repl_pw: Secret-123
        users:
          - name: mel
            pw: melpw123
```
Used Roles
--------------

License
-------
GNU General Public License v3.0

Author Information
------------------
Melanie Desaive
m.desaive@mailbox.org
