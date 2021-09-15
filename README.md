Ansible Role RSP Session Components
=========

[![build](https://github.com/grephappiness/rsp-session-components/actions/workflows/build.yml/badge.svg)](https://github.com/grephappiness/rsp-session-components/actions/workflows/build.yml)

Installs the Rstudio Server Pro session components binaries required for using Slurm with Rstudio Launcher. See https://docs.rstudio.com/rsw/integration/launcher-slurm/#8-install-rstudio-server-pro-session-components-on-slurm-compute-nodes

Requirements
------------

- Rstudio Server/Workbench Pro
- `rstudio-server` user account and group on all target hosts using the same UID/GID
- Slurm setup and configured on all target hosts including the rstudio-server host

Role Variables
--------------

Default values are set for the rsp version, rstudio-server user/group and default url to get the OS dependant binaries. 

```
rsp_version: "1.4.1717-3"

# it's assumed under session you have a subfolder for each distribution i.e. https://s3.amazonaws.com/rstudio-ide-build/session/xenial, centos7, etc
rsp_url: "https://s3.amazonaws.com/rstudio-ide-build/session" 

# rstudio-server user and group, change these to what common user/group your using for your rstudio-server configuration across all slurm nodes
rsp_rstudio_user: "rstudio-server"
rsp_rstudio_uid: 1001
rsp_rstudio_group: "rstudio-server"
rsp_rstudio_gid: 1001
```

Example Playbook
----------------

```
- hosts: rsp-servers
  roles:
   - { role: grephappiness.rsp-session-components }
```

License
-------

MIT / BSD

