Ansible ad-hoc commands are simple, one-liner commands that you can use to execute Ansible modules on remote hosts without writing a playbook. They're great for quick tasks like running shell commands, managing packages, or restarting services.

General Syntax of Ansible Ad-Hoc Commands:
bash

ansible <hosts> -i <inventory> -m <module> -a "<arguments>" [options]
<hosts>: The group of hosts or a single host where you want to run the command (e.g., all, webservers).
<inventory>: The inventory file that contains the list of hosts.
<module>: The Ansible module you want to use (e.g., ping, shell, command).
<arguments>: The arguments passed to the module (like a command to run).
Common Ad-Hoc Commands:
Ping All Hosts:


ansible all -i inventory.ini -m ping
This command pings all hosts in the inventory file to check connectivity.

Run a Shell Command on All Hosts:


ansible all -i inventory.ini -m shell -a "uptime"
This runs the uptime command on all hosts.

Install a Package:


ansible all -i inventory.ini -m apt -a "name=htop state=present" --become
Installs the htop package on all hosts using the apt module (for Debian/Ubuntu systems). --become is used to escalate privileges (like sudo).

Restart a Service:


ansible all -i inventory.ini -m systemd -a "name=nginx state=restarted" --become
Restarts the nginx service on all hosts using the systemd module.

Copy a File to Remote Hosts:


ansible all -i inventory.ini -m copy -a "src=/path/to/local/file dest=/path/to/remote/file" --become
Copies a file from the local machine to the remote hosts.

Get Information About Hosts (Facts):


ansible all -i inventory.ini -m setup
This command gathers and displays information (facts) about the remote hosts, like OS type, network interfaces, etc.

Check Free Disk Space:


ansible all -i inventory.ini -m shell -a "df -h"
Executes the df -h command on all hosts to check disk usage.

Using Ad-Hoc Commands with sudo:
If a command requires elevated privileges (like installing a package or restarting a service), you can use --become to escalate privileges (similar to sudo):


ansible all -i inventory.ini -m shell -a "your-command" --become
Ad-hoc commands are ideal for quick tasks where writing a playbook might be overkill. Let me know if you'd like more examples or help with specific tasks!






