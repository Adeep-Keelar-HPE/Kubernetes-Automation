# Pre-set variable
ansible = ansible-playbook 

build: 
	@echo "Starting the Ansible Automation."
	@echo "Starting the Pre Setup Tasks"
	${ansible} -i inventory/hosts playbooks/pre_setup.yml
	@echo "Ending the Pre Setup Tasks"
	@echo "Starting the Pre Check Tasks"
	${ansible} -i inventory/hosts playbooks/pre_checks.yml
	@echo "Ending the Pre Check Tasks"
	@echo "Starting Container Pre Check Tasks"
	${ansible} -i inventory/hosts playbooks/container_pre_checks.yml
	@echo "Ending Container Pre Checks"
	@echo "Setting up containerd"
	${ansible} -i inventory/hosts playbooks/setup_containerd.yml
	@echo "Downloading the Kubernetes packages."
	${ansible} -i inventory/hosts playbooks/kubernetes_installation.yml