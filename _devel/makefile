vagrant_up :
	vagrant up --no-provision

vagrant_provision :
	rm -rf tmp_roles
	rm -f ansible_php
	mkdir -p tmp_roles
	ln -s ../ ansible_php
	vagrant provision
	rm -rf tmp_roles
	rm -f ansible_php

clean :
	rm -rf tmp_roles
	rm -f ansible_php
	vagrant -f destroy

test :  vagrant_up vagrant_provision

travis_ci:
	sudo apt-get install software-properties-common
	sudo apt-add-repository -y ppa:ansible/ansible
	sudo apt-get update
	sudo apt-get install -y ansible
	ansible --version
	mkdir -p tmp_roles
	ln -s ../ ansible_php
	ansible-playbook -c local -e "hosts=localhost" test.yml
	rm -f ansible_php
