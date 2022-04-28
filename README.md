# wildcard-tls-playbook
Grabs certificates from Let's Encrypt, retrieves and encrypts them, then distributes them as needed.

## Requirements
* A "bastion" host which will store the keys and update Git with them
* Hosts to distribute TLS keys and certificates to
* Ansible 2.9+

## Usage
* Create a bastion host.
* Install Git on your bastion host.
* Generate some SSH keys on your bastion host for use with Git.
* Create a Git repository to hold certificate materials, add your bastion host's keys to it as access keys with write privileges, and clone it to `wildcard-tls-materials` in your user's $HOME on your bastion host (for the user you'll login with via Ansible).