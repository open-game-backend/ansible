# Open Game Backend Ansible Playbook
[Ansible playbook](https://docs.ansible.com/ansible/latest/user_guide/intro_getting_started.html) used for deploying the Open Game Backend.

# Setup

1. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-debian) on your control node. We can confirm that running Ansible from [Windows Subsystem for Linux](https://www.microsoft.com/store/productId/9MSVKQC78PK6) works perfectly fine.
1. Copy ```hosts.example``` to ```hosts``` and edit the ```hosts``` inventory file to include the names or URLs of the servers you want to deploy.
1. Create a [GitHub personal access token](https://github.com/settings/tokens) with the ```read:packages``` scope for downloading the Open Game Backend packages.
1. Copy ```group_vars/vault.example``` to ```group_vars/vault``` and edit the ```group_vars/vault``` file setting all necessary variables. Don't forget to [encrypt your vault](https://docs.ansible.com/ansible/latest/user_guide/vault.html#encrypting-existing-files).
1. Open Game Backend uses third-party rules in its playbook. You might need to add the following Ansible repositories:
    1. ```ansible-galaxy collection install community.general```
    1. ```ansible-galaxy install nginxinc.nginx``` (see https://github.com/nginxinc/ansible-role-nginx#installation)
    1. ```ansible-galaxy install elastic.elasticsearch,7.9.3``` (see https://github.com/elastic/ansible-elasticsearch#usage)
    1. ```ansible-galaxy install elastic.beats,7.9.3``` (see https://github.com/elastic/ansible-beats#usage)
    1. ```ansible-galaxy install fedelemantuano.kibana```(see https://github.com/fedelemantuano/ansible-kibana#usage)

# Hosts

Example hosts file for Amazon AWS:

```
[registry]
ec2-11-222-33-44.eu-central-1.compute.amazonaws.com ansible_connection=ssh ansible_user=ec2-user
```

# Deployment

To deploy the Open Game Backend, run the playbook like this:

```
ansible-playbook -i hosts site.yml --ask-become-pass --ask-vault-pass --verbose
```
