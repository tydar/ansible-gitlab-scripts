<<<<<<< HEAD
# Gitlab Runner Ansible Scripts

This is a small collection of quickly put-together ansible scripts to set up Gitlab runners with the shell executor environment properly configured to build my KVM Conjurer project.

## Usage

Each script can be invoked with the `ansible-playbook` command. The configuration of the Python 3 build environment on the Debian VMs I use requires specifying the Python 3 interpreter:

```
$ ansible-playbook -i inventories/some-inventory.yml \
                   -e 'ansible_python_interpreter=/usr/bin/python3' \
                   configure-conjurer-buildenv.yml   \
```

To safely store the tokens used in registering a Gitlab runner, I use an `ansible-vault` encrypted file:

```
$ cat YOUR_PASSWORD_HERE > secrets/keys.yml
$ ansible-vault encrypt --vault-id ID@vaultpasswdfile secrets/keys.yml
$ ansible-playbook -i inventories/some-inventory.yml \
                   -e secrets/keys.yml               \
                   --vault-id ID@vaultpasswdfile     \
                   configure-gitlab-runner.yml       \
```
=======
# ansible-gitlab-scripts
Basic scripts to configure my home gitlab testing environment.

I would not use these scripts to set up an actual production environment. For example--I am particularly concerned that the build environment
setup is fragile.

You need to provide your own inventory to ''ansible-playbook'' with the ''-i'' option. For the build environment setup script to work, the
inventory should specify a python3 interpreter as ansible_python_interpreter.

# TODO items:
* use ansible vault to provide secrets for gitlab-runner playbook to register runner with gitlab instance.
* parameterize basic-deb-setup script to allow for different initial users
* develop some way to automate the debian install process from the start (use a disk image instead of ISO?)
>>>>>>> e6e2331a1ae39fdc85b27be020e4813d612d7345
