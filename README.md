# Ansible Homelab (Public Version)
This Ansible project is designed to automate the setup and management of my homelab composed of three Debian nodes. The main node runs on arm64 (raspberrypi 4), while the other two nodes are on amd64 architecture. This project includes roles to configure storage, backup solutions, Docker, and more, ensuring efficient and reliable operation of the homelab.


## Roles
- storage_mount: Creates a RAID0 array with multiple drives and sets up a filesystem mount. (mainserver only)

- samba: Configures an SMB server for network file sharing. (mainserver only)

- seaweedfs: Sets up SeaweedFS with replication for Docker Swarm storage, ensuring data redundancy across all nodes.

- docker: Installs Docker, initializes the swarm, and joins the slave nodes to the swarm.

- deploy_containers: Deploys containers within the Docker Swarm. (mainserver only)

- setup_backups: Creates a daily backup script for Docker container storage and RAID array files. (mainserver only)

- wireguard: Sets up a WireGuard VPN server and generates client configuration files. (mainserver only)


## Prerequisites

- All nodes must run Debian OS (other OS are untested!).

- Ensure SSH access is configured for Ansible to communicate with the nodes.

- Python and Ansible installed on the control machine.


## Installation

#### Clone the repository:

```
git clone https://github.com/yourusername/ansible-homelab.git

cd ansible-homelab
```
<br />

#### Update the Inventory:

Modify the hosts inventory file to include your node details. Group the main server under mainservers and the other nodes under slaves.

```
[mainservers]
192.168.1.5 ansible_host=192.168.1.5

[slaves]
192.168.1.10 ansible_host=192.168.1.10
192.168.1.11 ansible_host=192.168.1.11

[all:vars]
ansible_user=raul
```
<br />

#### Update Variables:

Adjust any necessary variables in the "group_vars" folder to match your environment.
<br />

#### Update Removed Secrets:

This repository is a public version of my homelab deployments, and as such all the sensitive data has been removed.
All the removed sections can be found by searching the following in the project folder:

```
# Removed for obvious reasons
```


## Usage

#### Run the Playbook:

```
ansible-playbook -i hosts main.yml
```


## Contributing

Contributions are welcome! Please submit a pull request with detailed information about your changes!


## License

This project is licensed under the MIT License. See the LICENSE file for more information.