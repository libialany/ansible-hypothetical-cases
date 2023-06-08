## Start to Manage Ansible

**_what is Ansible_**


Ansible is a tool for configuration management and deployment of applications
Systems of the infrastructure by selecting Inventory(host set up).


Ansible utilities have the capability to control a set of files (directories) to manage other nodes by SSH.


**Format** playbooks are in YAML format.


**_Ansible Concepts_**

*Control* node any machine with Ansible.

*Manage* Nodes or hosts are managed by control node

*Inventory* file contains a list of hosts/managed nodes

*Modules* inside a Tasks it's run modules.

*Tasks* units of action in Ansible.

Note: A single task can be executed once with an ad-hoc command.

**__Use Case__**

Installing docker and docker-compose

**Playbook:** [playbook-docker-compose.yml](https://github.com/libialany/ansible-hypothetical-cases/blob/main/playbook-docker-compose.yml)

```
ansible-playbook -K playbook-docker-compose.yml
```

*_you want to automate your docker installation_*

setup this part in this playbook [playbook-docker-compose.yml](https://github.com/libialany/ansible-hypothetical-cases/blob/main/playbook-docker-compose.yml):

the hosts machines 

**Case install in your own machine**

```
---
- hosts: localhost
  connection: local
  become: yes
```

the become: yes = root user

for a simple case like get environment variables try this:


```
---
- hosts: localhost
  connection: local
```

test with a simple example:
 
```
---
- hosts: localhost
  connection: local
  tasks:
    - name: Basic usage
      ansible.builtin.debug:
        msg: "'{{ lookup('ansible.builtin.env', 'MEL') }}' is the HOME environment variable."
```

some importantant lines:

the distro GNU/Linux: 

```
    docker_gpg_url: https://download.docker.com/linux/(CHANGE THIS PART)/gpg
    docker_repo: deb https://download.docker.com/linux/(CHANGE THIS PART) bullseye stable
    docker_packges:
```

**Case install in a ec2**

```
ansible-playbook playbook-docker-compose.yml -u ubuntu
```

changing some part of the code:

```
---
- hosts: all
  become: yes
  vars:
```

**all scripts are explained**: [material](https://github.com/libialany/ansible-hipotetical-cases/blob/main/ebook-Ansible-security.pdf)

![alt text](https://github.com/libialany/ansible-hipotetical-cases/blob/main/1.PNG)

**Read more** : [Theory](https://sksonukushwaha403.medium.com/ansible-use-cases-and-advantages-f35515ffabe1)
