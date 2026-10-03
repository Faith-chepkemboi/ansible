# KijaniKiosk - Vagrant & Ansible

First Ansible project - 3 VMs deployed.

Servers:
- api: 192.168.56.10
- payments: 192.168.56.11
- logs: 192.168.56.12

Run:
vagrant up
ansible-playbook site.yml

Result: All 3 sites live in browser.
