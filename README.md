## A minimal example to reproduce the "Using `notify` with an `include` statement silently fails" bug

### Usage:

    ansible-playbook -i <host>, test.yml

### Expected results:

    [tadej@tlinux64 Bug reproducers]$ ansible-playbook -i salomon, test.yml 

    PLAY [all] ******************************************************************** 

    GATHERING FACTS *************************************************************** 
    ok: [salomon]

    TASK: [task in foo.yml] ******************************************************* 
    changed: [salomon] => {
        "changed": true, 
        "msg": "This is a testing task"
    }

    NOTIFIED: [test handler] ****************************************************** 
    ok: [salomon] => {
        "msg": "SUCCESS The test handler was run!"
    }

    PLAY RECAP ******************************************************************** 
    salomon                    : ok=3    changed=1    unreachable=0    failed=0

### Actual results:

    [tadej@tlinux64 Bug reproducers]$ ansible-playbook -i salomon, test.yml 

    PLAY [all] ******************************************************************** 

    GATHERING FACTS *************************************************************** 
    ok: [salomon]

    TASK: [task in foo.yml] ******************************************************* 
    changed: [salomon] => {
        "changed": true, 
        "msg": "This is a testing task"
    }

    PLAY RECAP ******************************************************************** 
    salomon                    : ok=2    changed=1    unreachable=0    failed=0

