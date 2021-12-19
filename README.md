# Docker Setup
Ansible Role to deploy a basic docker installation on a linux server.


**Tested:**
* Debian 11

## Functionality

To keep it short => it will set-up docker like described [here](https://docs.docker.com/engine/install/debian/).

There is also an option to install docker-compose on the target host.

* **Package installation**
  * Docker prerequisites
  * Docker base-packages


  * **Default opt-outs**:
    * docker-compose

## Info

* **Note:** this role currently only supports debian-based systems

## Usage

### Execution

Run the playbook:
```bash
ansible-playbook -K -D -i inventory/hosts.yml playbook.yml
```
