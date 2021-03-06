# Docker Ansible Environment

## Description

This project utilizes docker-compose to start an ansible container and a seperate debian-based target host.
This provides an isolated ansible environment, useful for testing ansible configurations, and avoiding the need for target VMs, physical hosts or local installations.

## Usage

### Start the containers

`docker-compose build && docker-compose up -d`

### Running playbooks

The ansible container mounts local directory playbooks/ as a volume. Playbooks can therefore be added or updated locally in playbooks/ without the need to restart the ansible container.

Run the example jenkins playbook present in directory playbooks/:

`docker exec -ti ansible ansible-playbook playbooks/jenkins_playbook.yaml`

This will install jenkins and its dependencies in container target_host_1.

Once installed you can navigate to jenkins interface at http://localhost:8080/

### Adding additional target hosts

Create additional target host containers by adding new entries to file docker-compose.yaml and the hosts file.


