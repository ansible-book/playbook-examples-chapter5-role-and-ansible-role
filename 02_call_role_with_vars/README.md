
在本目录下，执行下面的命令来查看测试结果:

```
ansible-playbook site*.yml
```

----------

请参考输出的结果:
```
ansible-playbook site_with_vars.yml
```
结果为：
```
[jshi@jjshi 02_call_role_with_vars]$ ansible-playbook site_with_vars.yml

PLAY [all] *********************************************************************

TASK [setup] *******************************************************************
ok: [localhost]

TASK [my_role_with_vars : echo external var] ***********************************
ok: [localhost] => {
    "msg": "External variable 'ex_param':Hello from ex_param for the 1st time"
}

TASK [my_role_with_vars : echo internal param1] ********************************
ok: [localhost] => {
    "msg": "External variable 'in_param1':Hello internal param1"
}

TASK [my_role_with_vars : echo external param2] ********************************
ok: [localhost] => {
    "msg": "internal variable 'in_param2':Hello internal param2"
}

TASK [my_role_with_vars : echo internal in_sys_param] **************************
ok: [localhost] => {
    "msg": "External variable 'in_sys_param':x86_64"
}

TASK [my_role_with_vars : echo external var] ***********************************
ok: [localhost] => {
    "msg": "External variable 'ex_param':Hello from ex_param for the 2nd time"
}

TASK [my_role_with_vars : echo internal param1] ********************************
ok: [localhost] => {
    "msg": "External variable 'in_param1':This is the value from external"
}

TASK [my_role_with_vars : echo external param2] ********************************
ok: [localhost] => {
    "msg": "internal variable 'in_param2':Hello internal param2"
}

TASK [my_role_with_vars : echo internal in_sys_param] **************************
ok: [localhost] => {
    "msg": "External variable 'in_sys_param':x86_64"
}

PLAY RECAP *********************************************************************
localhost                  : ok=9    changed=0    unreachable=0    failed=0  

```
