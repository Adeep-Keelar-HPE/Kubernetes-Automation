## To setup the SSH Keys for the Ansible

* Identify the SSH Keys Available in the System.

  `ls ~/.ssh`

* Start the SSH Agent and add the correct key to SSH Agent.
    ```
    eval $(ssh-agent -s)
    ssh-add ~/.ssh/id_ed25519
    ```
* Copy the Public Key to the Remote Server.

  `ssh-copy-id -i ~/.ssh/id_ed25519.pub <remote-server-user>@<remote-server-ip>`

* Update the Inventory Appropriately.
