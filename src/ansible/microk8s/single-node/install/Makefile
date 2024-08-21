run:
	ANSIBLE_PYTHON_INTERPRETER=/usr/bin/python3.12 ansible-playbook -i inventory/hosts playbooks/pre-setup.yml
	ANSIBLE_PYTHON_INTERPRETER=/usr/bin/python3.12 ansible-playbook -i inventory/hosts playbooks/microk8s_install.yml