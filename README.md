# cloudify-ansible-plugin-custom-module-example
A simple Ansible plugin with custom module example

the blueprint will connect to a host and execute Ansible playbook on that host

it will use a custom module called custom_diff that checks 2 values if they are equal or not

you can clone it on manager host
https://github.com/ahmadiesa-abu/ansible_custom_diff_module

and provide the path to it to the blueprint input `custom_module_location`
