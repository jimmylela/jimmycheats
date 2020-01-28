

Inventory

Ansible reads information about which machines you want to manage from your inventory. Although you can pass an IP address to an ad-hoc command, you need inventory to take advantage of the full flexibility and repeatability of Ansible.
Action: create a basic inventory

For this basic inventory, edit (or create) /etc/ansible/hosts 


Configuration settings

Configuration settings include both values from the ansible.cfg file and environment variables. Within this category, values set in configuration files have lower precedence. Ansible uses the first ansible.cfg file it finds, ignoring all others. Ansible searches for ansible.cfg in these locations in order:

        ANSIBLE_CONFIG (environment variable if set)
        ansible.cfg (in the current directory)
        ~/.ansible.cfg (in the home directory)
        /etc/ansible/ansible.cfg


Command-line options

Any command-line option will override any configuration setting.

When you type something directly at the command line, you may feel that your hand-crafted values should override all others, but Ansible does not work that way. Command-line options have low precedence - they override configuration only. They do not override playbook keywords, variables from inventory or variables from playbooks.

You can override all other settings from all other sources in all other precedence categories at the command line by Using -e extra variables at the command line, but that is not a command-line option, it is a way of passing a variable.


Playbook keywords

Any playbook keyword will override any command-line option and any configuration setting.

Within playbook keywords, precedence flows with the playbook itself; the more specific wins against the more general:

    play (most general)
    blocks/includes/imports/roles (optional and can contain tasks and each other)
    tasks (most specific)


Variables

Any variable will override any playbook keyword, any command-line option, and any configuration setting.

Variables that have equivalent playbook keywords, command-line options, and configuration settings are known as Connection variables. Originally designed for connection parameters, this category has expanded to include other core variables like the temporary directory and the python interpreter.

Connection variables, like all variables, can be set in multiple ways and places. You can define variables for hosts and groups in inventory. You can define variables for tasks and plays in vars: blocks in playbooks. However, they are still variables - they are data, not keywords or configuration settings. Variables that override playbook keywords, command-line options, and configuration settings follow the same rules of variable precedence as any other variables.

