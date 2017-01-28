
在本目录下，执行下面的命令来查看测试结果:

```
ansible-playbook site.yml
```

在Playbook文件site.yml中，调用了两个role：db和web。这两个role都依赖role common，不过Ansible会识别出重复的依赖，执行一次role common。

请参考输出的结果:

```
[jshi@jjshi 01-dependent-same-role-without-variable]$ ansible-playbook site.yml

PLAY [apply common configuration to all nodes] *********************************

TASK [setup] *******************************************************************
ok: [localhost]

TASK [common : Task in role common] ********************************************
ok: [localhost] => {
    "msg": "No variable is required in this role"
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
