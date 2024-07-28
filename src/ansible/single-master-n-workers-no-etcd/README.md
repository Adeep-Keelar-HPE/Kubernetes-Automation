# Single Master N Workers No ETCD Automation Setup

## File Structure

```
├── Makefile
├── ansible.cfg
├── inventory
│   ├── group_vars
│   │   ├── master.yml
│   │   └── worker.yml
│   └── hosts
├── playbooks
│   └── pre_setup.yml
└── roles
    ├── README.md
    ├── pre_checks
    └── pre_setup
        ├── README.md
        └── tasks
            ├── main.yml
            └── pre_setup_tasks.yml
```

__NOTE:__ The Inventory and the Host needs to be generated. The scripts will be provided for its automation. 
