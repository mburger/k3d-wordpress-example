# example k8s based wordpress setup

the provided setup was tested on a linux machine, the binaries committed into lfs are thus
also linux binaries for x86_64, if you are running on a different os / arch please visit the following links
to find your correct download

* ctlptl -> https://github.com/tilt-dev/ctlptl/releases
* k3d -> https://github.com/k3d-io/k3d/releases
* kubectl -> https://kubernetes.io/docs/tasks/tools/

either simply replace the binaries in the tools folder for yourself or place them somewhere else in your $PATH

additionally make sure ansible is installed on your machine with whatever method you prefer, please see
https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html for details

# what do you need to do?

```
# only if you want to use tools placed in the _tools folder
source .env
# NOTE: the step below will modify your kubeconfig! do yourself a favour and make a backup if you
# don't have any yet, just in case :)
# this will create the local k3d installation and setup your kubeconfig to use it
# usually this will take around 60 seconds (depending on your machine + internet connection)
# so go and grab a coffe ;)
ctlptl apply -f _support/k3d.yaml
cd ansible
ansible-playbook main.yml
# simply open the site http://wordpress.tset.localho.st in your favourite browser of choice
xdg-open http://wordpress.tset.localho.st
```

when you don't need the local k3d installation anymore execute ctlptl delete -f _support/k3d.yaml to delete it again
