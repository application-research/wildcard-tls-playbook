# wildcard-tls-playbook
Grabs certificates from Let's Encrypt, retrieves and encrypts them, then distributes them as needed.

Uses [go-acme/lego](https://github.com/go-acme/lego/).

## Requirements
* A "bastion" host which will talk to DNS and Let's Encrypt to retrieve and store certificates
* Hosts to distribute TLS keys and certificates to
* Ansible 2.12+

## Usage
Preparation:

* Create a bastion host.
* Create a Git repository to hold certificate materials
* Create a "bin" directory in your user directory and add it to your PATH if you don't already have that setup.

Hint: `export PATH=$PATH:~/bin` in ~/.bashrc :)

* Copy vars/dns-secrets.yaml.dist to vars/dns-secrets.yaml and edit it
* Create an inventory under `inventories` and edit it to match your environment
* Create a Vault Secret and call it vars/vault-secret. This will be used to encrypt the TLS keys and certificates. MAKE SURE TO BACK IT UP.
* Accept the Let's Encrypt ToS by setting "LE_ACCEPT_TOS: true" in $inventory/group_vars/all.yaml

Running the playbook:

`ansible-playbook site.yml --vault-password-file vars/vault-secret -i inventories/inventory`