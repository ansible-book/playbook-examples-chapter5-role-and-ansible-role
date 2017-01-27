
在本目录下，执行下面的命令来查看测试结果:


```
ansible-playbook site*.yml
```
----------
当前目录子目录roles下面的role，一直可以成功被调用。无论role location相关的设置是什么。
```
ansible-playbook site_call_role_in_current_subfolder_roles.yml
```
----------
下面的role成功执行需要，设置环境变量ANSIBLE_ROLES_PATH:
```
ansible-playbook site_call_role_in_env_ANSIBLE_ROLE_PATH.yml
```
设置方法：

```
export ANSIBLE_ROLES_PATH=./location_defined_in_env_ANSIBLE_ROLES_PATH
```
----------
下面的命令成功执行需要，执行unset环境变量ANSIBLE_ROLES_PATH，并且在当前目录下的ansible.cfg中设置roles_path

```
ansible-playbook site_call_role_in_configuration_file_ansible_cfg.yml
```

```
unset ANSIBLE_ROLES_PATH
```
在ansible.cfg下面添加roles_path的设置如下
```
roles_path = ./location_defined_in_configuration_file_ansible_cfg
```
----------

下面的命令成功执行需要，执行unset环境变量ANSIBLE_ROLES_PATH，并且所有的ansible.cfg文件没有关于roles_path变量的设置：

```
ansible-playbook site_call_role_in_etc_ansible_roles.yml
```

```
unset ANSIBLE_ROLES_PATH
```
在ansible.cfg下面*注释掉*roles_path的设置如下，同时保证你的其它ansible配置文件也没有关于roles_path的设置：
```
#roles_path = ./location_defined_in_configuration_file_ansible_cfg
```
