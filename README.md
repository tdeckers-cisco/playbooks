### Ansible Playbooks

This assume you have manually bootstrapped a machine with Ansible.

Get Ansible [here](https://github.com/ansible/ansible).
```
# take care of dependencies
yum -y install  python-setuptools python-devel gcc openssh-clients git
easy_install pip
pip install paramiko PyYAML jinja2
git clone -b release1.4.1 https://github.com/ansible/ansible.git
cd ansible
make install
```

Maintain an ansible [inventory](http://www.ansibleworks.com/docs/intro_inventory.html) file `/etc/ansible/hosts`.  This file is in 
INI format.

```
[docker]
192.168.1.20    ansible_ssh_user=root ansible_ssh_password=secret
```
_Note: the ssh user/password and other configurations are optional._

You can turn off [host key checking](http://www.ansibleworks.com/docs/intro_getting_started.html#host-key-checking) if desired by adding following section in `/etc/ansible/ansible.cfg`:
```
[defaults]
host_key_checking = False
```

Use ansible-playbook to run.

