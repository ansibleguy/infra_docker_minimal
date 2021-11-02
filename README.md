# Docker Setup
Ansible role to set-up basic docker on a linux host

**Note:** this role currently only supports debian-based systems

**Tested:**
* Debian 11

## Functionality

To keep it short => it will set-up docker like described [here](https://docs.docker.com/engine/install/debian/).

There is also an option to install docker-compose on the target host.

* Package installation
  * Docker prerequisites
  * Docker base-packages
  * Optional: docker-compose

## Usage

Run the playbook:
```bash
ansible-playbook -K -D -i inventory/hosts.yml playbook.yml
```
