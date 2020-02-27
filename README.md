# cloudify-ansible-plugin-custom-module-example
A simple Ansible plugin with custom module example

the blueprint will connect to a host and execute Ansible playbook on that host

it will use a custom module called custom_diff that checks 2 values if they are equal or not

you can clone it on manager host
https://github.com/ahmadiesa-abu/ansible_custom_diff_module

and provide the path to it to the blueprint input `custom_module_location`


execution result :
```
cfy events list 9c6d7f6a-d010-433e-a815-778316eeb1cf --tail
Listing events for execution id 9c6d7f6a-d010-433e-a815-778316eeb1cf [include_logs=True]
2020-02-27 10:48:54.315  CFY <TestCustom> Starting 'install' workflow execution
2020-02-27 10:48:54.956  CFY <TestCustom> [vm_gdzitt] Validating node instance before creation: nothing to do
2020-02-27 10:48:55.066  CFY <TestCustom> [vm_gdzitt] Precreating node instance: nothing to do
2020-02-27 10:48:55.178  CFY <TestCustom> [vm_gdzitt] Creating node instance: nothing to do
2020-02-27 10:48:55.261  CFY <TestCustom> [vm_gdzitt] Configuring node instance: nothing to do
2020-02-27 10:48:55.374  CFY <TestCustom> [vm_gdzitt] Starting node instance: nothing to do
2020-02-27 10:48:55.591  CFY <TestCustom> [vm_gdzitt] Creating agent
2020-02-27 10:48:55.825  CFY <TestCustom> [vm_gdzitt.create] Sending task 'cloudify_agent.installer.operations.create'
2020-02-27 10:48:59.794  LOG <TestCustom> [vm_gdzitt.create] INFO: Creating Agent vm_gdzitt
2020-02-27 10:49:06.572  LOG <TestCustom> [vm_gdzitt.create] INFO: Agent created, configured and started successfully
2020-02-27 10:49:07.466  CFY <TestCustom> [vm_gdzitt.create] Task succeeded 'cloudify_agent.installer.operations.create'
2020-02-27 10:49:07.572  CFY <TestCustom> [vm_gdzitt] Agent created
2020-02-27 10:49:07.626  CFY <TestCustom> [vm_gdzitt] Plugins installed
2020-02-27 10:49:07.937  CFY <TestCustom> [vm_gdzitt] Poststarting node instance: nothing to do
2020-02-27 10:49:08.314  CFY <TestCustom> [vm_gdzitt] Node instance started
2020-02-27 10:49:08.850  CFY <TestCustom> [test-custom-module_9kabe3] Validating node instance before creation: nothing to do
2020-02-27 10:49:08.964  CFY <TestCustom> [test-custom-module_9kabe3] Precreating node instance: nothing to do
2020-02-27 10:49:09.047  CFY <TestCustom> [test-custom-module_9kabe3] Creating node instance: nothing to do
2020-02-27 10:49:09.322  CFY <TestCustom> [test-custom-module_9kabe3] Configuring node instance
2020-02-27 10:49:09.566  CFY <TestCustom> [test-custom-module_9kabe3.configure] Sending task 'cloudify_ansible.tasks.set_playbook_config'
2020-02-27 10:49:12.193  CFY <TestCustom> [test-custom-module_9kabe3.configure] Task succeeded 'cloudify_ansible.tasks.set_playbook_config'
2020-02-27 10:49:12.476  CFY <TestCustom> [test-custom-module_9kabe3] Node instance configured
2020-02-27 10:49:12.640  CFY <TestCustom> [test-custom-module_9kabe3] Starting node instance: nothing to do
2020-02-27 10:49:12.693  CFY <TestCustom> [test-custom-module_9kabe3] Poststarting node instance: nothing to do
2020-02-27 10:49:12.807  CFY <TestCustom> [test-custom-module_9kabe3] Establishing relationships
2020-02-27 10:49:13.116  CFY <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] Sending task 'cloudify_ansible.tasks.run'
2020-02-27 10:49:15.009  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: Writing this data to temp file: {u'vms': {u'hosts': {u'vm': {u'ansible_ssh_common_args': u'-o StrictHostKeyChecking=no', u'ansible_become': True, u'ansible_ssh_private_key_file': '/tmp/tmp5Hygsg/cbd228e6-594e-11ea-bc9c-fa163e68b583', u'ansible_host': u'10.239.3.28', u'ansible_user': u'centos'}}}}
2020-02-27 10:49:15.047  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: Process created, PID: 12530
2020-02-27 10:49:19.426  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> ansible-playbook 2.9.5
2020-02-27 10:49:19.427  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>   config file = /etc/ansible/ansible.cfg
2020-02-27 10:49:19.427  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>   configured module search path = [u'/tmp/ansible-modules/modules']
2020-02-27 10:49:19.427  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>   ansible python module location = /opt/mgmtworker/env/plugins/default_tenant/cloudify-ansible-plugin-2.7.1/lib/python2.7/site-packages/ansible
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>   executable location = /usr/bin/ansible-playbook
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>   python version = 2.7.5 (default, Jun 20 2019, 20:27:34) [GCC 4.8.5 20150623 (Red Hat 4.8.5-36)]
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> Using /etc/ansible/ansible.cfg as config file
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> PLAYBOOK: playbook.yaml ********************************************************
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> 1 plays in /tmp/tmp5Hygsg/playbook/playbook.yaml
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> PLAY [Testing Custom Module] ***************************************************
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> TASK [Gathering Facts] *********************************************************
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> task path: /tmp/tmp5Hygsg/playbook/playbook.yaml:1
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> ok: [vm]
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> META: ran handlers
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>
2020-02-27 10:49:19.428  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> TASK [first case test] *********************************************************
2020-02-27 10:49:19.430  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> task path: /tmp/tmp5Hygsg/playbook/playbook.yaml:4
2020-02-27 10:49:19.430  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> changed: [vm] => {"changed": true}
2020-02-27 10:49:19.431  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>
2020-02-27 10:49:19.431  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> TASK [dump first test output] **************************************************
2020-02-27 10:49:19.433  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> task path: /tmp/tmp5Hygsg/playbook/playbook.yaml:11
2020-02-27 10:49:19.433  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> ok: [vm] => {
2020-02-27 10:49:19.434  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>     "msg": {
2020-02-27 10:49:19.434  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>         "changed": true,
2020-02-27 10:49:19.435  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>         "diff": {
2020-02-27 10:49:19.435  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>             "source": "cloudify",
2020-02-27 10:49:19.435  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>             "target": "Cl0udify"
2020-02-27 10:49:19.435  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>         },
2020-02-27 10:49:19.435  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>         "failed": false
2020-02-27 10:49:19.435  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>     }
2020-02-27 10:49:19.436  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> }
2020-02-27 10:49:19.436  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>
2020-02-27 10:49:19.437  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> TASK [second case test] ********************************************************
2020-02-27 10:49:19.437  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> task path: /tmp/tmp5Hygsg/playbook/playbook.yaml:14
2020-02-27 10:49:19.438  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> ok: [vm] => {"changed": false}
2020-02-27 10:49:19.438  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>
2020-02-27 10:49:19.439  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> TASK [dump second test output] *************************************************
2020-02-27 10:49:19.439  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> task path: /tmp/tmp5Hygsg/playbook/playbook.yaml:21
2020-02-27 10:49:19.440  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> ok: [vm] => {
2020-02-27 10:49:19.440  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>     "msg": {
2020-02-27 10:49:19.440  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>         "changed": false,
2020-02-27 10:49:19.441  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>         "diff": {
2020-02-27 10:49:19.441  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>             "source": "/bin/bash",
2020-02-27 10:49:19.442  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>             "target": "/bin/bash"
2020-02-27 10:49:19.442  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>         },
2020-02-27 10:49:19.442  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>         "failed": false
2020-02-27 10:49:19.442  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>     }
2020-02-27 10:49:19.443  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> }
2020-02-27 10:49:19.444  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>
2020-02-27 10:49:19.444  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> TASK [third case test] *********************************************************
2020-02-27 10:49:19.444  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> task path: /tmp/tmp5Hygsg/playbook/playbook.yaml:24
2020-02-27 10:49:19.445  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> changed: [vm] => {"changed": true}
2020-02-27 10:49:19.446  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>
2020-02-27 10:49:19.447  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> TASK [dump third test output] **************************************************
2020-02-27 10:49:19.447  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> task path: /tmp/tmp5Hygsg/playbook/playbook.yaml:31
2020-02-27 10:49:19.447  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> ok: [vm] => {
2020-02-27 10:49:19.447  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>     "msg": {
2020-02-27 10:49:19.448  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>         "changed": true,
2020-02-27 10:49:19.448  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>         "diff": {
2020-02-27 10:49:19.448  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>             "source": "manager5.openstacklocal\n",
2020-02-27 10:49:19.448  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>             "target": "manager5.openstacklocal"
2020-02-27 10:49:19.449  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>         },
2020-02-27 10:49:19.449  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>         "failed": false
2020-02-27 10:49:19.450  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>     }
2020-02-27 10:49:19.450  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> }
2020-02-27 10:49:19.450  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> META: ran handlers
2020-02-27 10:49:19.451  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> META: ran handlers
2020-02-27 10:49:19.451  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>
2020-02-27 10:49:19.451  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> PLAY RECAP *********************************************************************
2020-02-27 10:49:19.452  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out> vm                         : ok=7    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
2020-02-27 10:49:19.452  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: <out>
2020-02-27 10:49:19.491  LOG <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] INFO: Execution done (PID=12530, return_code=0): /usr/bin/ansible-playbook -vv -i /tmp/tmp5Hygsg/playbook/hosts --extra-vars='@/tmp/tmpJaF7P3'  /tmp/tmp5Hygsg/playbook/playbook.yaml
2020-02-27 10:49:20.344  CFY <TestCustom> [test-custom-module_9kabe3->vm_gdzitt|establish] Task succeeded 'cloudify_ansible.tasks.run'
2020-02-27 10:49:20.578  CFY <TestCustom> [test-custom-module_9kabe3] Relationships established
2020-02-27 10:49:20.631  CFY <TestCustom> [test-custom-module_9kabe3] Node instance started
2020-02-27 10:49:20.978  CFY <TestCustom> 'install' workflow execution succeeded
Finished executing workflow install on deployment TestCustom

```
