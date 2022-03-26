# Ansible

# Introduction

Ansible is the DevOps tool used for configuration management, automation, orchestration, and managing IT Infrastructure. 

Ansible is an automation engine that automates repetitive, cumbersome, and complex tasks such as cloud provisioning, application deployment, and configuration management.

---

[https://docs.ansible.com/ansible/latest/index.html#about-ansible](https://docs.ansible.com/ansible/latest/index.html#about-ansible)

# Necessity and benefits

---

![image](https://www.notion.so/Ansible-fa0f781b799e4f9fa09ce17ed28e386b#4f740f954afb48bc95ddf1a6749afebf)

- **Free**: Ansible is an open-source tool.
- **Very simple to set up and use**: No special [coding](https://www.simplilearn.com/tutorials/programming-tutorial/coding-for-beginners) skills are necessary to use Ansible’s playbooks (more on playbooks later).
- **Powerful**: Ansible lets you model even highly complex IT workflows.
- **Flexible**: You can orchestrate the entire application environment no matter where it’s deployed. You can also customize it based on your needs.
- **Agentless**: You don’t need to install any other software or firewall ports on the client systems you want to automate. You also don’t have to set up a separate management structure.
- **Efficient**: Because you don’t need to install any extra software, there’s more room for application resources on your server.

# Use cases | Comparison with it's alternatives.

---

Ansible has various use cases in Provisioning, Configuration Management, Application Deployment, Continuous Deployment, Automation, and Orchestration. So, if you are looking forward to a career in DevOps, IT automation, and managing cloud infrastructure then Ansible is a must-have.

- **Provisioning**: Provisioning is creating new infrastructure. Ansible allows for application management, deployment, orchestration, and configuration management.
- **Continuous Delivery**: Ansible provides a simpler way to automatically deploy applications. All required services for a deployment can be configured from a single system. Continuous Integration (CI) tool can be used to run Ansible playbook which can be used to test and automatically deploy the application to production if tests are passed.
- **Application Deployment**: Ansible provides a simpler way to deploy applications across the infrastructure. Deployment of multi-tier applications can be simplified and the infrastructure can be easily changed over time.
- **Ansible for Cloud Computing**: Ansible makes it easy to provision instances across all cloud providers. Ansible contains multiple modules and allows to manage of large cloud infrastructure across the public-private and hybrid cloud.
- **Ansible for Security and Compliance**: You can define security policies in Ansible which will automate security policy across all machines in the network. Security roles once configured in an Ansible node will be embedded across all machines in the network automatically.

![Untitled](Ansible%204f740/Untitled%201.png)

# **Why do we need Ansible?**

[https://k21academy.com/ansible/ansible-for-beginners/#:~:text=Ansible has various use cases,Ansible is a must-have](https://k21academy.com/ansible/ansible-for-beginners/#:~:text=Ansible%20has%20various%20use%20cases,Ansible%20is%20a%20must%2Dhave).

- Ansible allows you to write scripts that describe the state of your system. That means once written these scripts are re-usable and reliable.
- Ansible scripts are written in YAML. Ansible uses the same tools that are normally used for administration in Linux systems.
- Ansible gives you the power to manage multi-tier deployments.
- Ansible can be easily introduced to the existing environment.
- Ansible is built for the cloud. Modules included in Ansible help manage deployments across AWS, Azure, and other cloud services

# Architecture

---

![Untitled](./Ansible 4f740/untitled.png)

- **Modules**: Modules are script-like programs written to specify the desired state of the system. These are typically written in a code editor. Modules are written by the developer and executed via SSH. Modules are part of a larger program called Playbook. Ansible module is a standalone script that can be used inside an Ansible Playbook.
- **Plugins**: Plugins are pieces of code that enhance the core functionality of Ansible. Plugins execute on the control node.
- **Inventory**: Ansible reads information about the machines you manage from the inventory. Inventory is listed in the file which contains IP addresses, databases, and servers.
- **Playbook**: Playbooks are files written in YAML. Playbooks describe the tasks to be done by declaring configurations in order to bring a managed node into the desired state.

# Ansible setup and hands-on

---

example of ansible playbook :

```
---
- hosts: webservers
vars:
http_port: 80
max_clients: 200
remote_user: root
tasks:
- name: ensure apache is at the latest version
yum: name=httpd state=latest
- name: write the apache config file
template: src=/srv/httpd.j2 dest=/etc/httpd.conf
notify:
- restart apache
- name: ensure apache is running (and enable it at boot)
service: name=httpd state=started enabled=yes
handlers:
- name: restart apache
service: name=httpd state=restarted
```

# Installation

---

[https://docs.ansible.com/ansible/latest/installation_guide/index.html](https://docs.ansible.com/ansible/latest/installation_guide/index.html)

# Requirements

---

[https://docs.ansible.com/ansible-tower/2.2.2/html/installandreference/requirements_refguide.html](https://docs.ansible.com/ansible-tower/2.2.2/html/installandreference/requirements_refguide.html)

# How ansible works

---

Ansible works by connecting to other machines (nodes) and executes programs called modules. Modules are small programs that specify the desired state of the system. Ansible removes modules after execution.

# **[Variable precedence: Where should I put a variable?](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#id39)**

You can set multiple variables with the same name in many different places. When you do this, Ansible loads every possible variable it finds, then chooses the variable to apply based on variable precedence. In other words, the different variables will override each other in a certain order.

Teams and projects that agree on guidelines for defining variables (where to define certain types of variables) usually avoid variable precedence concerns. We suggest that you define each variable in one place: figure out where to define a variable, and keep it simple. For examples, see [Tips on where to set variables](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#variable-examples).

Some behavioral parameters that you can set in variables you can also set in Ansible configuration, as command-line options, and using playbook keywords. For example, you can define the user Ansible uses to connect to remote devices as a variable with `ansible_user`, in a configuration file with `DEFAULT_REMOTE_USER`, as a command-line option with `-u`, and with the playbook keyword `remote_user`. If you define the same parameter in a variable and by another method, the variable overrides the other setting. This approach allows host-specific settings to override more general settings. For examples and more details on the precedence of these various settings, see [Controlling how Ansible behaves: precedence rules](https://docs.ansible.com/ansible/latest/reference_appendices/general_precedence.html#general-precedence-rules).

[Using Variables - Ansible Documentation](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable)

# Roles Ansible

---

Roles let you automatically load related vars, files, tasks, handlers, and other Ansible artifacts based on a known file structure. After you group your content in roles, you can easily reuse them and share them with other users.

[https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html)

# Ansible Galaxy

---

[https://galaxy.ansible.com/docs/](https://galaxy.ansible.com/docs/)

# Ansible Templating

---

Ansible uses Jinja2 templating to enable dynamic expressions and access to [variables](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#playbooks-variables)
 and [facts](https://docs.ansible.com/ansible/latest/user_guide/playbooks_vars_facts.html#vars-and-facts)
. You can use templating with the [template module](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/template_module.html#template-module)
. For example, you can create a template for a configuration file, then deploy that configuration file to multiple environments and supply the correct data (IP address, hostname, version) for each environment. You can also use templating in playbooks directly, by templating task names and more. You can use all the [standard filters and tests](https://jinja.palletsprojects.com/en/3.0.x/templates/#builtin-filters)
 included in Jinja2. Ansible includes additional specialized filters for selecting and transforming data, tests for evaluating template expressions, and [Lookup plugins](https://docs.ansible.com/ansible/latest/plugins/lookup.html#lookup-plugins)
 for retrieving data from external sources such as files, APIs, and databases for use in templating.

![Untitled](Ansible%204f740/Untitled%203.png)

[https://docs.ansible.com/ansible/2.5/user_guide/playbooks_templating.html](https://docs.ansible.com/ansible/2.5/user_guide/playbooks_templating.html)

[https://blog.knoldus.com/deploying-custom-files-with-ansible-jinja2-templates/](https://blog.knoldus.com/deploying-custom-files-with-ansible-jinja2-templates/)