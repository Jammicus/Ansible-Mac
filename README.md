# Simple Developer Mac Setup.


## Requirements
* Sudo permissions

The following needs to be installed on the host:
* XCode 
* XCode Command Line Tools (There is a hacky playbook here to install this, but I strongly advise not using it)

## Playbooks

| Playbook          | Default Install method| Brew Install option | Brew Install Override                                               |
| ----------------- | --------------------- | ------------------- | ------------------------------------------------------------------- |
| Ansible           | Pip                   | No                  | -                                                                   |  
| CommandLineTools  | Instal Script         | No                  | -                                                                    | 
| CMake             | Binary                | Yes                 | cmake_homebrew_install: true                                        |
| Doxygen           | Binary                | Yes                 | doxygen_homebrew_install: true                                      |
| Gawk              | Homebrew              | No                  | -                                                                   |
| Gnused            | Homebrew              | No                  | -                                                                   |
| Gnutar            | Homebrew              | No                  | -                                                                   |
| Gradle            | Binary                | No                  | -                                                                   |
| Homebrew          | Binary                | No                  | -                                                                   |
| Java              | Homebrew              | No                  | -                                                                   |
| Kotlin            | Binary                | Yes                 | kotlin_homebrew_install: true                                       |
| Libiconv          | Binary                | Yes                 | libiconv_homebrew_install: true                                     |
| Maven             | Binary                | Yes                 | maven_homebrew_install: true                                        |
| NodeJs            | Binary                | Yes                 | node_homebrew_install: true                                         |
| OpenSSL           | Binary                | Yes                 | openssl_homebrew_install: true                                      |
| Packer            | Binary                | Yes                 | packer_homebrew_install: true                                       |
| Pkgconfig         | Homebrew              | -                   | -                                                                   |
| Postman           | Binary                | Yes                 | postman_homebrew_install: true                                      |
| Python            | Binary (Both 2 and 3) | Yes                 | python_two_homebrew_install: true and python_three_homebrew_install |
| Terraform         | Binary                | Yes                 | terraform_homebrew_install                                          |
| Ulimit            | -                     | -                   | -                                                                   |
| Users             | -                     | -                   | -                                                                   |
| VisualStudioCode  | Binary                | Yes                 | vscode_homebrew_install: true                                       |
| Wget              | Binary                | Yes                 | wget_homebrew_install: true                                         |
| Yarn              | Binary                | Yes                 | yarn_homebrew_install: true                                         |

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

* I'm unable to update homebrew -> Remove the following from your ~/.bashrc and ~/.bash_profile files:

```
export HOMEBREW_NO_AUTO_UPDATE=1
```
