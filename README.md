vagrant up
export ANSIBLE_HOST_KEY_CHECKING=false
ansible-playbook --private-key=~/.ssh/vagrant_key --inventory-file=vagrant_inventory -v site.yml
