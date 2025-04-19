---
title: "Ansibel Playbook"
date:  2025-04-17T22:53:58+05:30
draft: false
github_link: "https://github.com/milanneupanee/ansible_playbook"
author: "Milan Neupane"
tags:
  - Ansible
  - Playbook
  - example
  - DevOps
image: /images/post.jpg
description: ""
toc:
---
---

# What is an Ansible Playbook?

An **Ansible Playbook** is a YAML file used to **define and execute automation tasks** on remote machines. It is the **heart of Ansible configuration management**, enabling infrastructure as code. Playbooks can describe a policy to be enforced or a set of steps in a general IT process.

Unlike scripts that run sequentially, **Playbooks are declarative**, meaning you define the desired state of your system rather than how to get there.

---

##  Structure of an Ansible Playbook

An Ansible Playbook is made up of:

- **Plays**: Each play targets a group of hosts and defines a list of tasks to run.
- **Tasks**: Each task executes a module with specific arguments.
- **Modules**: Reusable Ansible code blocks like `apt`, `copy`, `service`, etc.
- **Variables**: Used to store dynamic values.
- **Handlers**: Special tasks triggered by `notify` from other tasks.
- **Roles**: A way to organize playbooks into reusable components.

---

##  Example: A Basic Ansible Playbook

```yaml
---
- name: Install Apache on web servers
  hosts: webservers
  become: yes

  vars:
    apache_package: apache2

  tasks:
    - name: Update apt cache
      apt:
        update_cache: yes

    - name: Install Apache
      apt:
        name: "{{ apache_package }}"
        state: present

    - name: Ensure Apache is running
      service:
        name: "{{ apache_package }}"
        state: started
        enabled: yes
```

###  Explanation:

- `hosts: webservers`: Target all machines in the `webservers` group.
- `become: yes`: Run tasks with `sudo` privileges.
- `vars`: Define reusable variables.
- `tasks`: A list of actions to perform.

---

##  Handlers Example

Handlers are tasks triggered only when notified by another task (used for things like restarting services).

```yaml
- name: Configure Nginx
  hosts: nginx
  become: yes

  tasks:
    - name: Copy nginx config
      copy:
        src: nginx.conf
        dest: /etc/nginx/nginx.conf
      notify: Restart nginx

  handlers:
    - name: Restart nginx
      service:
        name: nginx
        state: restarted
```

---

##  Using Variables

Variables can be defined in the playbook, inventory, or external files.

```yaml
vars:
  app_user: deploy
  app_port: 8080
```

And then used like:

```yaml
- name: Add application user
  user:
    name: "{{ app_user }}"
```

---

##  Real-world Playbook with Multiple Plays

```yaml
---
- name: Install Docker on all hosts
  hosts: all
  become: yes

  tasks:
    - name: Install Docker dependencies
      apt:
        name: "{{ item }}"
        state: present
      loop:
        - apt-transport-https
        - ca-certificates
        - curl
        - software-properties-common

    - name: Add Docker GPG key
      apt_key:
        url: https://download.docker.com/linux/ubuntu/gpg
        state: present

    - name: Add Docker repository
      apt_repository:
        repo: deb https://download.docker.com/linux/ubuntu focal stable
        state: present

    - name: Install Docker
      apt:
        name: docker-ce
        state: present

- name: Deploy App Container
  hosts: appservers
  become: yes

  tasks:
    - name: Run nginx container
      docker_container:
        name: nginx
        image: nginx:latest
        state: started
        ports:
          - "80:80"
```

---

##  Best Practices

- Use **roles** to organize playbooks.
- Keep playbooks **idempotent** (safe to run multiple times).
- Use **variables** and **templates** to make playbooks dynamic.
- Use **handlers** to avoid unnecessary restarts.
- Always **test in staging** before applying to production.

---

##  Summary Table of Key Components

| Component     | Description                                                       | Example                          |
|---------------|-------------------------------------------------------------------|----------------------------------|
| `hosts`       | Group of machines to run the playbook on                         | `hosts: webservers`              |
| `tasks`       | Steps to be performed on the remote machines                     | `apt`, `copy`, `service`         |
| `vars`        | Define variables used in tasks                                   | `app_port: 8080`                 |
| `handlers`    | Tasks triggered by `notify`                                      | Restart services                 |
| `roles`       | Reusable and modular directories of playbooks                    | `roles/webserver/tasks/main.yml`|
| `become`      | Run tasks with sudo privileges                                   | `become: yes`                    |
| `loop`        | Iterate over a list                                              | `loop: [pkg1, pkg2]`             |

---

