# vagrant-ansible-opensearch
This vagrant box brings up an open search local service using ansible. It uses the OpenSearch project ansible playbook found here https://github.com/opensearch-project/ansible-playbook

## Requirements
To run this you will need the following:
- Vagrant
- Git

## Running
To bring up the environment run the following from a bash/ terminal window
```
git submodule init --update
vagrant up --provision --color
```

## Customization
You can customize this box by updating the `inventories/opensearch/hosts` file and `Vagrantfile`, adding or removing servers.
