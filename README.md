# Simple Developer Mac Setup.


## Requirements
* Sudo permissions

The following needs to be installed on the host:
* XCode 
* XCode Command Line Tools (There is a hacky playbook here to install this, but I strongly advise not using it)

## Playbooks

| Playbook          | Default Install method| Brew Install option | Brew Install Override                                               |
| ----------------- | --------------------- | ------------------- | ------------------------------------------------------------------- |
| Ansible           | Pip                   | No                  |                                                                     |  
| CommandLineTools  | Content Cell          |                     |                                                                     | 
| Doxygen           |                       |                     |                                                                     |
| Gawk              |                       |                     |                                                                     |
| Gnu-sed           |                       |                     |                                                                     |
| Gnu-tar           |                       |                     |                                                                     |
| Gradle            |                       |                     |                                                                     |
| Homebrew          |                       |                     |                                                                     |
| Java              |                       |                     |                                                                     |
| Kotlin            |                       |                     |                                                                     |
| Libiconv          |                       |                     |                                                                     |
| Maven             | Binary                | yes                 | maven_homebrew_install: true                                        |
| NodeJs            |                       |                     |                                                                     |
| OpenSSL           |                       |                     |                                                                     |
| Packer            |                       |                     |                                                                     |
| Pkgconfig         |                       |                     |                                                                     |
| Postman           |                       |                     |                                                                     |
| Python            | Binary (Both 2 and 3) | Yes                 | python_two_homebrew_install: true and python_three_homebrew_install |
| Terraform         |                       |                     |                                                                     |
| Ulimit            |                       |                     |                                                                     |
| VisualStudioCode  |                       |                     |                                                                     |
| Wget              |                       |                     |                                                                     |
| Yarn              |                       |                     |                                                                     |

## Running

## Updating Homebrew Versions

To prevent unexpected upgrades, links to homebrew packages configuration files are provided to each script. To update, update the URL to the version you want.

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

## FAQ

* I'm unable to update any of my homebrew packages -> Remove the following from your ~/.bashrc and ~/.bash_profile files:

```
export HOMEBREW_NO_AUTO_UPDATE=1
```
