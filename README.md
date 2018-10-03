# Simple Developer Mac Setup.


## Requirements
* Sudo permissions

The following needs to be installed on the host:
* XCode 
* XCode Command Line Tools (There is a hacky playbook here to install this, but I strongly advise not using it)

## Playbooks

## Running

## Testing

To test the playbooks, a vagrant file has been specified. The following commands can be used:

```
# Create the machine and run Ansible:
vagrant up
# Run ansible on an already running machine:
vagrant provision
# Remove/kill the vagrant machine
vagrant destroy --force
```
