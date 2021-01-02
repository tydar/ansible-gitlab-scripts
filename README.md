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
$ ansible-vault encrypt --vault-id ID@vaultpasswdfile secrets/keys.yml
$ ansible-playbook -i inventories/some-inventory.yml \
                   -e secrets/keys.yml               \
                   --vault-id ID@vaultpasswdfile     \
                   configure-gitlab-runner.yml       \
```

where `secrets/keys.yml` is of the format

```
gitlab_url=http://your.url.com
gitlab_api_token=YOUR_API_TOKEN
gitlab_runner_token=YOUR_RUNNER_REGISTRATION_TOKEN
```
