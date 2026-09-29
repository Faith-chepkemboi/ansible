# My First Ansible & Vagrant Automation Project

This repository documents my hands-on setup connecting **Ansible** to a local **Vagrant** virtual machine environment. 

## 🏗️ What I Configured & Learned

### 1. Vagrant Virtual Machine Management
I downloaded, initialized, and verified a local Ubuntu environment using the following core Vagrant workflow:
* `vagrant box add ubuntu/jammy64` - Downloaded the official Ubuntu 22.04 base image.
* `vagrant box list` - Verified the box was successfully downloaded locally.
* `vagrant up` - Bootstrapped and started the guest operating system.
* `vagrant status` - Checked the current operational state of the VM.
* `vagrant ssh-config` - Extracted the precise port and private key configurations required for external connections.

### 2. Infrastructure Configuration Files

#### `Vagrantfile`
Configured Vagrant to use the modern Ubuntu image and automatically hand off system provisioning to Ansible upon startup:
```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yaml"
  end
end
```

#### `ansible.cfg`
Customized Ansible's runtime behavior to automatically pinpoint the dynamic Vagrant inventory and bypass interactive host verification prompts:
```ini
[defaults]
inventory = ./inventory/hosts
remote_user = vagrant
host_key_checking = False
identity = /home/chepkemoi/Ansible/.vagrant/machines/default/virtualbox/private_key
port = 22
```

---

## 🚀 Execution & Verification
To execute the automated setup, run:
```bash
vagrant provision
```

### Successful Execution Status
```text
PLAY [all] *********************************************************************
TASK [Gathering Facts] *********************************************************
ok: [default]

TASK [check for connectivity] **************************************************
ok: [default]

PLAY RECAP *********************************************************************
default                    : ok=2    changed=0    unreachable=0    failed=0   
```
