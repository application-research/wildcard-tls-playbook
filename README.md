# wildcard-tls-playbook
Grabs certificates from Let's Encrypt, retrieves and encrypts them, then distributes them as needed.

## Requirements
* A "bastion" host which will talk to DNS and Let's Encrypt to retrieve and store certificates
* Hosts to distribute TLS keys and certificates to
* Ansible 2.9+

## Usage
Preparation:

* Create a bastion host.
* Create a Git repository to hold certificate materials
* Copy vars/dns-secrets.yaml.dist to vars/dns-secrets.yaml and edit it
* Accept the Let's Encrypt ToS
* Edit `inventory` and fill it with your hosts as appropriate

Running the playbook:
ansible-playbook site.yml -i inventory --vault-password-file vars/vault-secret
