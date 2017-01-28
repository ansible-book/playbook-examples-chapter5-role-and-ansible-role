
在本目录下，执行下面的命令来查看测试结果:

```
ansible-playbook site.yml
```

在Playbook文件site.yml中，调用了两个role：db和web。只执行一次role common。role web中的变量会在整个play中生效。不会后调用的role中的变量并没有覆盖之前的变量。

请参考输出的结果:

```
[jshi@jjshi 05-dependent-same-role-with-variable-in-both-roles]$ ansible-playbook site.yml

PLAY [apply common configuration to all nodes] *********************************

TASK [setup] *******************************************************************
ok: [localhost]

TASK [common : Task in role common] ********************************************
ok: [localhost] => {
    "msg": "Require variable name, the value is NameInDbVarsFile"
}

TASK [db : Task in role db] ****************************************************
ok: [localhost] => {
    "msg": "This is the task of db"
}

TASK [web : Task in role web] **************************************************
ok: [localhost] => {
    "msg": "This is the task in role web"
}

PLAY RECAP *********************************************************************
localhost                  : ok=4    changed=0    unreachable=0    failed=0   


```
