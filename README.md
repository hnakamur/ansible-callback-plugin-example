ansible-callback-plugin-example
===============================

An example of callback plugin for Ansible.
This plugin does not print `TASK [include ] *****` line.


```
$ ansible-playbook playbook.yml
 [WARNING]: provided hosts list is empty, only localhost is available


PLAY ***************************************************************************
 [WARNING]: Error when using <bound method CallbackModule.v2_playbook_on_task_start of </home/hnakamur/ansible-callback-plugin-
example/callback_plugins/skip_task_include_on_task_start.CallbackModule object at 0x7f9aac66be90>>: type object 'super' has no
attribute 'v2_playbook_on_task_start'

ok: [localhost]
included: /home/hnakamur/ansible-callback-plugin-example/included.yml for localhost
ok: [localhost] => {
    "msg": "hello"
}

PLAY RECAP *********************************************************************
localhost                  : ok=3    changed=0    unreachable=0    failed=0
```


```
$ mv ansible.cfg ansible.cfg.bak
$ ansible-playbook playbook.yml
 [WARNING]: provided hosts list is empty, only localhost is available


PLAY ***************************************************************************

TASK [setup] *******************************************************************
ok: [localhost]

TASK [include] *****************************************************************
included: /home/hnakamur/ansible-callback-plugin-example/included.yml for localhost

TASK [debug] *******************************************************************
ok: [localhost] => {
    "msg": "hello"
}

PLAY RECAP *********************************************************************
localhost                  : ok=3    changed=0    unreachable=0    failed=0
```

## Documents and sources

* [callbacks](http://docs.ansible.com/ansible/developing_plugins.html#callbacks)
* [Source code which prints `TASK [include\]`](https://github.com/ansible/ansible/blob/7960aa92ed81e09eefa1e878160984d5a6007f84/lib/ansible/plugins/callback/default.py#L126)
