
在本目录下，执行下面的命令来查看测试结果:

```
ansible-playbook site.yml
```

在Playbook文件site.yml中，调用了依次三个role comoon，db和web。db可以使用common中的变量，同样也可以使用web中的变量。

roles中的变量被引入play，在该role之前之后调用的role都可以使用该变量。db可以使用它之前调用的role common中的变量，同样可以调用之后的role中的变量web

请参考输出的结果:

```
[jshi@jjshi 06-use-variable-in-dependent-role]$ ansible-playbook site.yml

PLAY [apply common configuration to all nodes] *********************************

TASK [setup] *******************************************************************
ok: [localhost]

TASK [common : Task in role common] ********************************************
ok: [localhost] => {
    "msg": "Task in role common"
}

TASK [db : Task in role db] ****************************************************
ok: [localhost] => {
    "msg": "This is the task of db, echo variable server in common, common.sample.com"
}

TASK [db : Task in role db] ****************************************************
ok: [localhost] => {
    "msg": "This is the task of db, echo variable server in web, web.sample.com"
}

TASK [web : Task in role web] **************************************************
ok: [localhost] => {
    "msg": "This is the task in role web"
}

PLAY RECAP *********************************************************************
localhost                  : ok=5    changed=0    unreachable=0    failed=0   

```
