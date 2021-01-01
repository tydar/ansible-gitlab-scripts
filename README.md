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
