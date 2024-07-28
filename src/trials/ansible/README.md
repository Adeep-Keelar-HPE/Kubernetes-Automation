## To Generate the Inventory

* Identify the available SSH Keys. 

	`ls ~/.ssh`

* Add Correct Key to the SSH Agent. Here, my system has the ed_25519 keys.
	```
	eval $(ssh-agent -s)
	ssh-add ~/.ssh/id_ed25519
	```

* Copy Public Key to the Remote Server.

	`ssh-copy-id -i ~/.ssh/id_ed25519.pub <username-of-remote-server>@<ip-of-remote-server>`

* Manually generate the Inventory. (Automation will be set for this process)

	```
	[all]
	<ip-addr-1-remote-server> ansible_user=<user-name> ansible_ssh_private_key_file=<path>
	```
* Test by running Ansible command.
	`ansible all -i inventory -m ping`
