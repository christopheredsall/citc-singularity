# citc-singularity

Ansible playbook to add [Singularity](https://www.sylabs.io/guides/3.0/user-guide/index.html) to the [Cluster in the Cloud](https://cluster-in-the-cloud.readthedocs.io/en/latest/)

Clone this repo in to the location the cluster in the cloud looks for customisation playbooks

```ShellSession
[opc@mgmt ~]$ cd /mnt/shared/etc
[opc@mgmt etc]$ sudo mkdir -p ansible-playbooks
[opc@mgmt etc]$ sudo chown opc ansible-playbooks
[opc@mgmt etc]$ cd ansible-playbooks
[opc@mgmt ansible-playbooks]$ git clone https://github.com/christopheredsall/citc-singularity.git
```

Do a one off run on the management node

```ShellSession
[opc@mgmt ~]$ cd /mnt/shared/etc/ansible-playbooks/citc-singularity
[opc@mgmt citc-singularity]$ sudo ansible-playbook -i /root/hosts site.yml
```
