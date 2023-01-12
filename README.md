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

* **Note:** this role currently only supports debian-based systems

## Usage

### Execution

Run the playbook:
```bash
ansible-playbook -K -D -i inventory/hosts.yml playbook.yml
```
