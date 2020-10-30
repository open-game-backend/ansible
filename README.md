# Open Game Backend Ansible Playbook
[Ansible playbook](https://docs.ansible.com/ansible/latest/user_guide/intro_getting_started.html) used for deploying the Open Game Backend.

# Setup

1. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-debian) on your control node. We can confirm that running Ansible from [Windows Subsystem for Linux](https://www.microsoft.com/store/productId/9MSVKQC78PK6) works perfectly fine.
1. Copy ```hosts.example``` to ```hosts``` and edit the ```hosts``` inventory file to include the names or URLs of the servers you want to deploy.
1. Create a [GitHub personal access token](https://github.com/settings/tokens) with the ```read:packages``` scope for downloading the Open Game Backend packages.
1. Copy ```group_vars/vault.example``` to ```group_vars/vault``` and edit the ```group_vars/vault``` file setting all necessary variables. Don't forget to [encrypt your vault](https://docs.ansible.com/ansible/latest/user_guide/vault.html#encrypting-existing-files).

# Deployment

To deploy the Open Game Backend, run the playbook like this:

```
ansible-playbook -i hosts site.yml --ask-become-pass --ask-vault-pass --verbose
```
