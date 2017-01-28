用ansible-galaxy命令创建新的role

```
ansible-galaxy init first_demo -p ./roles
```

```
.
├── ansible.cfg
├── inventory.ini
├── README.md
├── roles
│   └── first_demo
│       ├── defaults
│       │   └── main.yml
│       ├── files
│       ├── handlers
│       │   └── main.yml
│       ├── meta
│       │   └── main.yml
│       ├── README.md
│       ├── tasks
│       │   └── main.yml
│       ├── templates
│       ├── tests
│       │   ├── inventory
│       │   └── test.yml
│       └── vars
│           └── main.yml
└── site.yml

```
