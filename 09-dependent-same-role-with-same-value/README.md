
在本目录下，执行下面的命令来查看测试结果:

```
ansible-playbook site.yml
```

在Playbook文件site.yml中，调用了两个role：db和web。这两个role都依赖role common，不过定义依赖时传入的值相同，所以Ansible会认为是重复的依赖，执行一次role common。

请参考输出的结果:

```
[jshi@jjshi 03-dependent-same-role-with-same-value]$ ansible-playbook site.yml

PLAY [apply common configuration to all nodes] *********************************

TASK [setup] *******************************************************************
ok: [localhost]

TASK [common : Task in role common] ********************************************
ok: [localhost] => {
    "msg": "Require variable name, the value is SameName"
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
