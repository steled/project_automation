## Files
### ansible/host_vars/control.yml
```
---
# file: host_vars/control.yml
host:
  - hostname: <hostname>
    ip: <ip>
```

### ansible/host_vars/nodes.yml
```
---
# file: host_vars/nodes.yml
host:
  - hostname: <hostname>
    ip: <ip>
  - hostname: <hostname>
    ip: <ip>
  - hostname: <hostname>
    ip: <ip>
```

### ansible/roles/common/defaults/main.yml
```
---
# file: roles/common/defaults/main.yml
root_password: "md5 <root_password>"
timezone: Europe/Berlin
```

### ansible/roles/gitea/defaults/main.yml
```
---
# file: roles/gitea/default/main.yml
gitea_version: "1.11"
gitea_arch: "linux-arm-6"

gitea_user: gitea
gitea_comment: "Gitea User"
gitea_group: gitea
gitea_home: /home/gitea
gitea_shell: /bin/bash

gitea_bin: /usr/local/bin/gitea
gitea_work_dir: /var/lib/gitea

# template: gitea.app.ini.j2
gitea_app_name: "Gitea: Git with a cup of tea"
gitea_run_mode: prod

## [oauth2]
gitea_jwt_secret: "<jwt_secret>"

## [security]
gitea_inernal_token: "<internal_token>"
gitea_install_lock: true
gitea_secret_key: "<secret_key>"

## [database]
gitea_db_type: sqlite3
gitea_db_host: 127.0.0.1:3306
gitea_db_name: gitea
gitea_db_user: gitea
gitea_db_passwd: ""
gitea_db_ssl_mode: disable
gitea_db_charset: utf8
gitea_db_path: "{{ gitea_work_dir }}/data/gitea.db"

## [repository]
#gitea_repository_root: "{{ gitea_home }}/gitea-repositories"
gitea_repository_root: "/ext/gitea"

## [server]
gitea_domain: <ip>
gitea_protocol: https
gitea_http_port: 443
gitea_redirect_other_port: true
gitea_cert_file: https/cert.pem
gitea_key_file: https/key.pem
gitea_disable_ssh: false
gitea_ssh_port: 22
gitea_lfs_start_server: true
gitea_lfs_content_path: "{{ gitea_work_dir }}/data/lfs"
gitea_lfs_jwt_secret: "<jwt_secret>"
gitea_offline_mode: true

## [mailer]
gitea_mailer_enabled: false

## [service]
gitea_register_email_confirm: false
gitea_enable_notify_mail: false
gitea_disable_registration: false
gitea_allow_only_external_registration: false
gitea_enable_captcha: false
gitea_require_signin_view: false
gitea_default_keep_emaill_private: false
gitea_default_allow_create_organization: true
gitea_default_enable_timetracking: true

## [picture]
gitea_disable_gravatar: true
gitea_enable_federated_avatar: false

## [openid]
gitea_enable_openid_signin: false
gitea_enable_openid_signup: false

## [session]
gitea_session_provider: file

## [log]
gitea_log_mode: file
gitea_log_level: info
gitea_log_root_path: "{{ gitea_work_dir }}/log"
```

### ansible/roles/glusterfs/defaults/main.ml
```
---
# file: roles/glusterfs/defaults/main.yml
brick_dir: /data/glusterfs/myvol1/brick1
gluster_vol: glustervol1
mount_dir: /mnt/gluster
gluster_replicas: 3
gluster_arbiters: 1

nodes:
  - <hostname>
  - <hostname>
  - <hostname>
```

### ansible/roles/pxeboot/defaults/main.yml
```
---
# file: roles/pxeboot/defaults/main.yml
nodes:
  - name: <hostname>
    sn: <sn>
  - name: <hostname>
    sn: <sn>
  - name: <hostname>
    sn: <sn>
```

### ansible/roles/user_config/defaults/main.yml
```
---
# file: roles/user_config/defaults/main.yml
users:
  - name: <usernam>
    state: present
    shell: /bin/bash
    key_file: "*.id_rsa.pub"
  - name: pi
    state: absent
    shell: /bin/bash
```