# Nginx node for ansible

[![CircleCI](https://img.shields.io/circleci/project/github/practical-ansible/nginx-node.svg)](https://circleci.com/gh/practical-ansible/nginx-node)
[![Quality](https://img.shields.io/ansible/quality/39746.svg)](https://galaxy.ansible.com/practical-ansible/nginx_node)
[![Downloads](https://img.shields.io/ansible/role/d/39746.svg)](https://galaxy.ansible.com/practical-ansible/nginx_node)

Deploy Node.js projects to Nginx with systemd. Orignial idea was to use uwsgi, but that is [not quite ready](https://uwsgi-docs.readthedocs.io/en/latest/V8.html) for this task. This role installs the nodejs application as systemd service.

## Prerequisities

* project artifact
* systemd on target machine
* npm > 5 on target machine because we use `npm ci` command

## Variables

|name|required|default|description|
|----|--------|-------|-----------|
|`node_archive`|no|(what you get from npm pack)|Path to the packaged application|
|`node_env_config`|no||Environment variables configuration|
|`node_group`|yes|www-data|Gropu name that runs the project on target machine|
|`node_max_fileupload_size`|yes|100M|Maximum file upload size for nginx|
|`node_project_environment`|yes|staging|Project environment name|
|`node_project_id`|no|(generated)|Project id to reference it in system settings|
|`node_project_name`|yes||Name of the project|
|`node_project_port`|yes||Port to run the node project on|
|`node_projects_directory`|yes|/var/www|Directory where you usually put projects on the target machine|
|`node_server_name`|yes||Hostname to reference the application
|`node_systemd_dir`|yes|/etc/systemd/system|Where your systemd services live
|`node_user`|yes|www-data|User name that runs the project on target machine|
|`node_version`|yes||Project version|

## TODO

* Read version from package.json
* Read project name from package.json
* Auto select port based on config
