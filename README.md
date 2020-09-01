# Docker Ansible Environment

## Description

This project utilizes docker-compose to start an ansible container and a seperate debian-based host container to which you can apply ansible configurations.
This provides an isolated ansible environment on your local machine, useful for testing ansible configurations without the need for target VMs or physical hosts.

## Usage

### Deploy the containers

`docker-compose build && docker-compose up -d

### Running playbooks

Run the example jenkins playbook present in directory playbooks/

`docker exec -ti ansible ansible-playbook playbooks/jenkins_playbook.yaml`

Running this playbook will install jenkins and its dependecies in container target_host_1

Once installed you can navigate to jenkins interface at http://localhost:8080/

You can add more playbooks in playbooks/ without the need to restart the ansible container.

## Adding additional target hosts

If required, you create more target host containers by adding new entries to the docker-compose-yaml. Be sure if you do this to also add them to the hosts files so that ansible is aware of the new target host.

`

