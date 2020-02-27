# cloudify-ansible-plugin-custom-module-example
A simple Ansible plugin with custom module example

the blueprint will connect to a host and execute Ansible playbook on that host

it will use a custom module called custom_diff that checks 2 values if they are equal or not

you can clone it on manager host
https://github.com/ahmadiesa-abu/ansible_custom_diff_module

and provide the path to it to the blueprint input `custom_module_location`


execution result :
```
cfy events list be8431ea-9249-434d-a93c-ca6417feadef --tail
Listing events for execution id be8431ea-9249-434d-a93c-ca6417feadef [include_logs=True]
2020-02-27 11:27:58.481  CFY <ttt> Starting 'install' workflow execution
2020-02-27 11:27:59.085  CFY <ttt> [vm_eop714] Validating node instance before creation: nothing to do
2020-02-27 11:27:59.161  CFY <ttt> [vm_eop714] Precreating node instance: nothing to do
2020-02-27 11:27:59.256  CFY <ttt> [vm_eop714] Creating node instance: nothing to do
2020-02-27 11:27:59.362  CFY <ttt> [vm_eop714] Configuring node instance: nothing to do
2020-02-27 11:27:59.472  CFY <ttt> [vm_eop714] Starting node instance: nothing to do
2020-02-27 11:27:59.683  CFY <ttt> [vm_eop714] Creating agent
2020-02-27 11:27:59.928  CFY <ttt> [vm_eop714.create] Sending task 'cloudify_agent.installer.operations.create'
2020-02-27 11:28:04.593  LOG <ttt> [vm_eop714.create] INFO: Creating Agent vm_eop714
2020-02-27 11:28:12.111  LOG <ttt> [vm_eop714.create] INFO: Agent created, configured and started successfully
2020-02-27 11:28:12.790  CFY <ttt> [vm_eop714.create] Task succeeded 'cloudify_agent.installer.operations.create'
2020-02-27 11:28:12.817  CFY <ttt> [vm_eop714] Agent created
2020-02-27 11:28:12.934  CFY <ttt> [vm_eop714] Plugins installed
2020-02-27 11:28:13.261  CFY <ttt> [vm_eop714] Poststarting node instance: nothing to do
2020-02-27 11:28:13.446  CFY <ttt> [vm_eop714] Node instance started
2020-02-27 11:28:14.168  CFY <ttt> [test-custom-module_3bvt2j] Validating node instance before creation: nothing to do
2020-02-27 11:28:14.338  CFY <ttt> [test-custom-module_3bvt2j] Precreating node instance: nothing to do
2020-02-27 11:28:14.425  CFY <ttt> [test-custom-module_3bvt2j] Creating node instance: nothing to do
2020-02-27 11:28:14.720  CFY <ttt> [test-custom-module_3bvt2j] Configuring node instance
2020-02-27 11:28:14.993  CFY <ttt> [test-custom-module_3bvt2j.configure] Sending task 'cloudify_ansible.tasks.set_playbook_config'
2020-02-27 11:28:17.586  CFY <ttt> [test-custom-module_3bvt2j.configure] Task succeeded 'cloudify_ansible.tasks.set_playbook_config'
2020-02-27 11:28:17.641  CFY <ttt> [test-custom-module_3bvt2j] Node instance configured
2020-02-27 11:28:17.955  CFY <ttt> [test-custom-module_3bvt2j] Starting node instance: nothing to do
2020-02-27 11:28:18.021  CFY <ttt> [test-custom-module_3bvt2j] Poststarting node instance: nothing to do
2020-02-27 11:28:18.146  CFY <ttt> [test-custom-module_3bvt2j] Establishing relationships
2020-02-27 11:28:18.435  CFY <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] Sending task 'cloudify_ansible.tasks.run'
2020-02-27 11:28:20.317  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: Writing this data to temp file: {u'vms': {u'hosts': {u'vm': {u'ansible_ssh_common_args': u'-o StrictHostKeyChecking=no', u'ansible_become': True, u'ansible_ssh_private_key_file': '/tmp/tmpP00wBJ/41bbd016-5954-11ea-bb70-fa163e68b583', u'ansible_host': u'10.239.3.28', u'ansible_user': u'centos'}}}}
2020-02-27 11:28:20.350  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: Process created, PID: 17608
2020-02-27 11:28:24.754  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> ansible-playbook 2.9.3
2020-02-27 11:28:24.755  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>   config file = /etc/ansible/ansible.cfg
2020-02-27 11:28:24.755  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>   configured module search path = [u'/tmp/ansible-modules/modules']
2020-02-27 11:28:24.755  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>   ansible python module location = /usr/lib/python2.7/site-packages/ansible
2020-02-27 11:28:24.755  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>   executable location = /usr/bin/ansible-playbook
2020-02-27 11:28:24.755  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>   python version = 2.7.5 (default, Jun 20 2019, 20:27:34) [GCC 4.8.5 20150623 (Red Hat 4.8.5-36)]
2020-02-27 11:28:24.755  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> Using /etc/ansible/ansible.cfg as config file
2020-02-27 11:28:24.755  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>
2020-02-27 11:28:24.755  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> PLAYBOOK: playbook.yaml ********************************************************
2020-02-27 11:28:24.755  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> 1 plays in /tmp/tmpP00wBJ/playbook/playbook.yaml
2020-02-27 11:28:24.755  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>
2020-02-27 11:28:24.755  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> PLAY [Testing Custom Module] ***************************************************
2020-02-27 11:28:24.755  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> TASK [Gathering Facts] *********************************************************
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> task path: /tmp/tmpP00wBJ/playbook/playbook.yaml:1
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> ok: [vm]
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> META: ran handlers
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> TASK [first case test] *********************************************************
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> task path: /tmp/tmpP00wBJ/playbook/playbook.yaml:4
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> changed: [vm] => {"changed": true}
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> TASK [dump first test output] **************************************************
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> task path: /tmp/tmpP00wBJ/playbook/playbook.yaml:11
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> ok: [vm] => {
2020-02-27 11:28:24.756  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>     "msg": {
2020-02-27 11:28:24.757  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>         "changed": true,
2020-02-27 11:28:24.757  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>         "diff": {
2020-02-27 11:28:24.758  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>             "source": "cloudify",
2020-02-27 11:28:24.758  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>             "target": "Cl0udify"
2020-02-27 11:28:24.759  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>         },
2020-02-27 11:28:24.759  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>         "failed": false
2020-02-27 11:28:24.759  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>     }
2020-02-27 11:28:24.760  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> }
2020-02-27 11:28:24.760  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>
2020-02-27 11:28:24.761  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> TASK [second case test] ********************************************************
2020-02-27 11:28:24.761  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> task path: /tmp/tmpP00wBJ/playbook/playbook.yaml:14
2020-02-27 11:28:24.762  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> ok: [vm] => {"changed": false}
2020-02-27 11:28:24.764  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>
2020-02-27 11:28:24.765  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> TASK [dump second test output] *************************************************
2020-02-27 11:28:24.765  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> task path: /tmp/tmpP00wBJ/playbook/playbook.yaml:21
2020-02-27 11:28:24.766  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> ok: [vm] => {
2020-02-27 11:28:24.766  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>     "msg": {
2020-02-27 11:28:24.766  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>         "changed": false,
2020-02-27 11:28:24.769  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>         "diff": {
2020-02-27 11:28:24.769  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>             "source": "/bin/bash",
2020-02-27 11:28:24.769  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>             "target": "/bin/bash"
2020-02-27 11:28:24.769  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>         },
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>         "failed": false
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>     }
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> }
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> TASK [third case test] *********************************************************
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> task path: /tmp/tmpP00wBJ/playbook/playbook.yaml:24
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> changed: [vm] => {"changed": true}
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> TASK [dump third test output] **************************************************
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> task path: /tmp/tmpP00wBJ/playbook/playbook.yaml:31
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> ok: [vm] => {
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>     "msg": {
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>         "changed": true,
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>         "diff": {
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>             "source": "manager5.openstacklocal\n",
2020-02-27 11:28:24.770  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>             "target": "manager5.openstacklocal"
2020-02-27 11:28:24.771  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>         },
2020-02-27 11:28:24.771  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>         "failed": false
2020-02-27 11:28:24.771  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>     }
2020-02-27 11:28:24.771  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> }
2020-02-27 11:28:24.771  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> META: ran handlers
2020-02-27 11:28:24.771  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> META: ran handlers
2020-02-27 11:28:24.771  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>
2020-02-27 11:28:24.771  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> PLAY RECAP *********************************************************************
2020-02-27 11:28:24.771  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out> vm                         : ok=7    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
2020-02-27 11:28:24.771  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: <out>
2020-02-27 11:28:24.794  LOG <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] INFO: Execution done (PID=17608, return_code=0): /usr/bin/ansible-playbook -vv -i /tmp/tmpP00wBJ/playbook/hosts --extra-vars='@/tmp/tmpGuNu9D'  /tmp/tmpP00wBJ/playbook/playbook.yaml
2020-02-27 11:28:25.684  CFY <ttt> [test-custom-module_3bvt2j->vm_eop714|establish] Task succeeded 'cloudify_ansible.tasks.run'
2020-02-27 11:28:25.931  CFY <ttt> [test-custom-module_3bvt2j] Relationships established
2020-02-27 11:28:26.153  CFY <ttt> [test-custom-module_3bvt2j] Node instance started
2020-02-27 11:28:26.449  CFY <ttt> 'install' workflow execution succeeded
Finished executing workflow install on deployment ttt

```
