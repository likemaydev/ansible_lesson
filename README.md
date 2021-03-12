9 Lesson. Ansible
---------------

1.Install software:
```
ansible@ansible-ctl:~/ansible_lesson$ ansible-playbook pack_install.yml -i inventory -l web

PLAY [web] ***********************************************************************************************************************************************

TASK [Gathering Facts] ***********************************************************************************************************************************
ok: [ansible1]
ok: [ansible2]

TASK [install_app : Install Nginx Web Server on Debian Family] *******************************************************************************************
changed: [ansible1]
changed: [ansible2]

TASK [install_app : Install nano] ************************************************************************************************************************
changed: [ansible1]
changed: [ansible2]

TASK [install_app : Install ftp-server] ******************************************************************************************************************
changed: [ansible1]
changed: [ansible2]

RUNNING HANDLER [install_app : nginx systemd] ************************************************************************************************************
ok: [ansible1]
ok: [ansible2]

RUNNING HANDLER [install_app : proftpd systemd] **********************************************************************************************************
ok: [ansible1]
ok: [ansible2]

PLAY RECAP ***********************************************************************************************************************************************
ansible1                   : ok=6    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
ansible2                   : ok=6    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

2Create user.
```
ansible@ansible-ctl:~/ansible_lesson$ ansible-playbook create_user.yml -i inventory -l web

PLAY [web] ***********************************************************************************************************************************************

TASK [Gathering Facts] ***********************************************************************************************************************************
ok: [ansible1]
ok: [ansible2]

TASK [create_user : Add group "students" to remote server] ***********************************************************************************************
changed: [ansible1]
changed: [ansible2]

TASK [create_user : Add user "student" to remote server] *************************************************************************************************
[WARNING]: The input password appears not to have been hashed. The 'password' argument must be encrypted for this module to work properly.
changed: [ansible1]
changed: [ansible2]

TASK [create_user : Create directory test_dir1] **********************************************************************************************************
changed: [ansible1]
changed: [ansible2]

TASK [create_user : Create directory test_dir2] **********************************************************************************************************
changed: [ansible1]
changed: [ansible2]

PLAY RECAP ***********************************************************************************************************************************************
ansible1                   : ok=5    changed=4    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
ansible2                   : ok=5    changed=4    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

3.Get server info:
```
ansible@ansible-ctl:~/ansible_lesson$ ansible-playbook hw_info.yml -i inventory -l web

PLAY [web] ***********************************************************************************************************************************************

TASK [Gathering Facts] ***********************************************************************************************************************************
ok: [ansible1]
ok: [ansible2]

TASK [hw_info : Show hostname] ***************************************************************************************************************************
ok: [ansible1] => {
    "ansible_hostname": "ansible1"
}
ok: [ansible2] => {
    "ansible_hostname": "ansible2"
}

TASK [hw_info : network info] ****************************************************************************************************************************
ok: [ansible1] => {
    "msg": [
        "All Interface List: ['lo', 'ens4']",
        "All IP: ['10.128.0.20']",
        "Gateway: 10.128.0.1",
        "Eth0 MAC: 42:01:0a:80:00:14",
        ""
    ]
}
ok: [ansible2] => {
    "msg": [
        "All Interface List: ['lo', 'ens4']",
        "All IP: ['10.128.0.21']",
        "Gateway: 10.128.0.1",
        "Eth0 MAC: 42:01:0a:80:00:15",
        ""
    ]
}

TASK [hw_info : HW info] *********************************************************************************************************************************
ok: [ansible1] => {
    "msg": [
        "CPU: ['0', 'GenuineIntel', 'Intel(R) Xeon(R) CPU @ 2.30GHz']",
        "CPU Core: 1",
        "RAM: 3683",
        "SWAP: 0",
        ""
    ]
}
ok: [ansible2] => {
    "msg": [
        "CPU: ['0', 'GenuineIntel', 'Intel(R) Xeon(R) CPU @ 2.30GHz']",
        "CPU Core: 1",
        "RAM: 3683",
        "SWAP: 0",
        ""
    ]
}

TASK [hw_info : GCP info] ********************************************************************************************************************************
ok: [ansible1] => {
    "msg": [
        "Cloud: Google Compute Engine",
        "Serial: GoogleCloud-0A3F707279E2F7C8AC5B729ACB207BDD",
        "UUID: 0a3f7072-79e2-f7c8-ac5b-729acb207bdd",
        ""
    ]
}
ok: [ansible2] => {
    "msg": [
        "Cloud: Google Compute Engine",
        "Serial: GoogleCloud-67CC8A952828F1D7DA1B44FD433A9EF2",
        "UUID: 67cc8a95-2828-f1d7-da1b-44fd433a9ef2",
        ""
    ]
}

PLAY RECAP ***********************************************************************************************************************************************
ansible1                   : ok=5    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
ansible2                   : ok=5    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

```
