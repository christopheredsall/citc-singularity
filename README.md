# citc-singularity

Ansible playbook to add [Singularity](https://www.sylabs.io/guides/3.0/user-guide/index.html) to the [Cluster in the Cloud](https://cluster-in-the-cloud.readthedocs.io/en/latest/)

## Install

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
## Usage

Obtain or build a container in your home directory

```ShellSession
[ce16990@mgmt ~]$  singularity pull docker://godlovedc/lolcow
```

Construct a Slurm job script:

```bash
#! /bin/bash

#SBATCH --job-name=cowsay
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=2
#SBATCH --cpus-per-task=1
#SBATCH --time=10:00

singularity exec lolcow.simg cowsay "Hello from Singularity on ${SLURM_JOB_NODELIST}"
```

Submit job, check output

```ShellSession
[ce16990@mgmt ~]$ sbatch cowsay.slm 
Submitted batch job 2
[ce16990@mgmt ~]$ cat slurm-2.out 
 ___________________________
/ Hello from Singularity on \
\ vm-standard2-2-ad1-0001   /
 ---------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```
