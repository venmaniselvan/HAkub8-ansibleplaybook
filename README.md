# HAkube8-ansibleplaybook
1. Prerequisites

  The account running this ansible playbook should have passwordless ssh account to all nodes (masters and slaves)
```
Masters are:
192.168.169.160
192.168.169.161
192.168.169.162

Workers are:
192.168.169.163
192.168.169.164
```

```
*****HOSTS********

[k8s:children]
k8snodes

# Set variables common for all k8s hosts
[k8s:vars]
ansible_ssh_user=root
ansible_become=true

[lead]
192.168.169.160
[masters]
192.168.169.161
192.168.169.162
[haproxy]
192.168.169.160
[workers]
192.168.169.163
192.168.169.164
[k8snodes]
192.168.169.160
192.168.169.161
192.168.169.162
192.168.169.163
192.168.169.164

```

2. Hosts

  Edit the hosts file to add or remove slave nodes, update the hostname and ip-address accordingly

3. Run the Playbook. Use this cmd
```
ansible-playbook -i hosts playbook.yml
```
