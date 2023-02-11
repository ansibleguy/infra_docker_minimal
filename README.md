# Ansible Role - Docker Setup
Ansible Role to deploy a basic docker installation on a linux server.

[![Ansible Galaxy](https://img.shields.io/ansible/role/56756)](https://galaxy.ansible.com/ansibleguy/infra_docker_minimal)
[![Ansible Galaxy Downloads](https://img.shields.io/badge/dynamic/json?color=blueviolet&label=Galaxy%20Downloads&query=%24.download_count&url=https%3A%2F%2Fgalaxy.ansible.com%2Fapi%2Fv1%2Froles%2F56756%2F%3Fformat%3Djson)](https://galaxy.ansible.com/ansibleguy/infra_docker_minimal)

**Tested:**
* Debian 11

## Install

```bash
ansible-galaxy install ansibleguy.infra_docker_minimal

# or to custom role-path
ansible-galaxy install ansibleguy.infra_docker_minimal --roles-path ./roles
```

## Functionality

To keep it short => it will set-up docker like described [here](https://docs.docker.com/engine/install/debian/).

There is also an option to install docker-compose on the target host.

* **Package installation**
  * Docker prerequisites
  * Docker base-packages


  * **Default opt-outs**:
    * docker-compose

  * **Default opt-ins**:
    * docker server component (_else only client will be installed_)

## Info

* **Note:** This role currently only supports debian-based systems

* **Note:** If you are using [NFTables](https://netfilter.org/projects/nftables/index.html) you will have problems running docker.

  Docker does not support NFTables natively. The 'docker-ce'/'docker-ce-cli' package has IPTables set as its dependency.

  One CAN keep the NFTables ruleset clean when running docker with the parameter 'iptables=false'. It is even cleaner if 'bridge=none' is set!

  After that only a few IPTables rules are added. To completely eliminate this docker-ruleset one needs to reload NFTables whenever docker is restarted.

  This Ansible role lets you configure this behaviour as can be seen in the example below!

  If you use NFTables you might also want to look into the [ansibleguy.infra_nftables](https://github.com/ansibleguy/infra_nftables) role!

## Usage

### Config

You can configure docker using the 'docker' variable/dictionary.

```yaml
docker:
  tcp:
    enable: true  # enable docker-service listening on tcp
    bind: '0.0.0.0'

  compose:
    enable: true  # install docker-compose
    version: '2.15.1'  # version of docker-compose to install

  nftables:
    clean: true  # set bridge_none, disable_iptables and reload to true
    bridge_none: false  # set bridge=none argument on docker-startup
    disable_iptables: false  # set iptables=false argument on docker-startup
    reload: false  # reload nftables after a docker.service restart to remove its auto-added iptables-rules
```

### Execution

Run the playbook:
```bash
ansible-playbook -K -D -i inventory/hosts.yml playbook.yml
```
