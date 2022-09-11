# vagrant-ansible-opensearch
This vagrant box brings up an open search local service using ansible. It uses the OpenSearch project ansible playbook found here https://github.com/opensearch-project/ansible-playbook

## Requirements
To run this you will need the following:
- Vagrant
- git
- Virtual Box

## Running
To bring up the environment run the following from a bash/ terminal window
```
git submodule init --update
vagrant up --provision --color
```
Then login to a browser from the host computer at http://10.0.10.14:5601 with the username "admin" and password set in the all.yml file (/inventories/opensearch/group_vars/all/all.yml).

To destroy the environment run the following from a bash/ terminal window
```
vagrant destroy -f
```

## Known issues
There are a few known issues that have pending pull requests in place on the ansible-playbook GitHub repository, these may need to be updated prior to running vagrant up:
- https://github.com/opensearch-project/ansible-playbook/pull/85/files
- https://github.com/opensearch-project/ansible-playbook/pull/81/files
```
cd ansible-playbook
git fetch origin pull/85/head:main
git cherry-pick 092faaa
git fetch origin pull/81/head:main
git cherry-pick 645147d
cd ..
```

Also the following will need to be added to wait for open search to start up before the task "Security Plugin configuration | Initialize the opensearch security index in opensearch" in the "/ansible-playbook/roles/linux/opensearch/tasks/security.yml".
```
- name: Pause for 1 minutes to start OpenSearch
  pause:
    minutes: 1
```
## Customization
You can customize this box by updating the `inventories/opensearch/hosts` file and `Vagrantfile`, adding or removing servers.
