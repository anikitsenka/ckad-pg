# Run platform via docker

We have prepared a docker image including all necessary dependencies and utilities .

You can use it to run exams or labs by following the instructions below or use  [video instructions](https://youtu.be/Xh6sWzafBmw)

### Run the docker container
```
sudo docker run --rm -it -v ~/.aws/:/root/.aws/ -v ~/learn/k8s/ckad-pg:/root/cks -w /root/cks viktoruj/runner

```

### Run your scenario

#### For single environment
````
TASK=01 make run_ckad_mock
````

### Delete your scenario

#### For single environment
```
TASK=01 make delete_ckad_mock
```

  [Video instruction for launching **CKAD mock exam**](https://youtu.be/7X4Y9QhbTsk)

### mock  CKAD exam
- choose [a mock exam](tasks%2Fckad%2Fmock)  number
- change **ubuntu_version** in ``{mock_number}/env.hcl`` if you need
- change instance type from ``spot`` to ``ondemand`` in  ``{mock_number}/env.hcl`` if you need
- create mock  CKAD exam ``TASK={mock_number} make run_ckad_mock`` or ``TASK={mock_number} make run_ckad_mock_clean`` if you'd like  to run with **clean** terragrunt cache
- find ``worker_pc_ip`` in ``terraform output``
- connect to ``worker_pc_ip``  with your ssh key and user ``ubuntu``
- open questions list ``{mock_number}/README.MD`` and do tasks
- use ``ssh  {kubernetes_nodename}`` from  work pc to connect to node
- run ``time_left`` on work pc to check time
- run ``check_result`` on work pc to check result
- delete mock  CKAD exam `make delete_ckad_mock`
- find exam solutions in ``{mock_number}/worker/files/solutions``  [mock 1 solutions](tasks%2Fckad%2Fmock%2F01%2Fworker%2Ffiles%2Fsolutions)   and [video](https://youtu.be/yQK7Ca8d-yw)
- find exam tests in ``{mock_number}/worker/files/tests.bats``
</details>