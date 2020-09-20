# WordPress Deployment Using Ansible 

- Requires [Ansible]( https://www.ansible.com/ ) 2.5 or newer
- Expects CentOS7 on AWS


These playbooks deploy a simple WordPress blogging platform, frontend by the Nginx web server and the
PHP-FPM process manager. To use, edit the hosts` file and add your server IP on which the application is to be deployed.
Please make sure the controller node can ssh to worker nodes using ssh keys.

## To make changes
        - To add variables i.e change wordpress username, database name, etc the file global_vars/all can be used
        - Secrets can be stored in the global_vars/vault.yml file. to edit the file use command 

  				ansible-vault edit global_vars/vault.yml

        - Password is stored in .vaultpass file on the home dir of the playbook.

NOTE: IF there is a error in playbook that states that host not found please use the command and Vault password can be found in .vaultpass file.

## Usage

Edit the hosts file and then run the playbook, like this:
```bash
	ansible-playbook site-playbook.yml
```
The playbooks will configure MySql, WordPress, Nginx, and PHP-FPM. When the run
is complete, the site can be access on the IP or domain that is entered in the global_vars ( the domain name needs to point to the IP ) and then one can begin the WordPress configuration.


To supply vault password in CLI use the command:

```bash
ansible-playbook site-playbook.yml -i hosts --ask-vault-pass

```
	
