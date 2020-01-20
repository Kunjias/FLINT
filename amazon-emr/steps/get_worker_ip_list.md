# get_worker_ip_list.sh

latest commit comment from original repository:
``` 
Initial commit of the provisioning scripts for an EMR cluster launch.

OBJECTIVE:
The purpose of this script is to get a list of the Worker Nodes in the cluster. 
We would like to obtain the private DNS names for each worker node so that we can debug them.
```

- line 31-34 (Print date-time, ```Starting Analysis```.)
- line 36 (Set ``` WORKERS_LIST_FILE ```)
- line 39,41-42 (```Get a list of the Worker nodes IP addresses```, print date-time as worker nodes are ready.)
- line 47-50 (Count and print number of worker nodes, print date-time and ```Done```.)
