# Pre-set variable
ansible = ansible-playbook 

build: 
	@echo "Starting the Ansible Automation."
	@echo "Starting the Pre Setup Tasks"
	${ansible} -i inventory/hosts playbooks/pre_setup.yml
	@echo "Ending the Pre Setup Tasks"