# get_worker_ip_list.sh

latest commit comment from original repository:
``` 
Initial commit of the provisioning scripts for an EMR cluster launch.
OBJECTIVE:
The purpose of this script is to get a list of the Worker Nodes in the cluster. 
We would like to obtain the private DNS names for each worker node so that we can debug them.
```
- Print date-time, ```Starting Analysis```.
- Get ```$WORKERS_LIST_FILE```.
- Get a list of the Worker nodes IP_Address, print date-time as worker nodes are ready.
- Count and print number of worker nodes, print date-time and ```Done```.
