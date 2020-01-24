# provision_worker_nodes.sh

latest commit comment from original repository:

```
VM Worker Node

#   OBJECTIVE:
#	The purpose of this script is to deploy a set of Virtual Machines (VMs) that will collectively act as a Spark
#	cluster.  The overall idea is to deploy an odd number of nodes that collectively form the Spark cluster. The
#	reason for the odd number is that one node will be the 'Master' node, and the remaining n-1 nodes will be the
#	workers (Spark Executors).
#
#	This script launches a series of VMs that will act as the Worker nodes.  Note that all this script does is copies
#	existing Master node VM configuration and replicates it so that we do not have to spend much time installing and
#	configuring the base Ubuntu installation — it was previously done when we setup the Master.
```

- line 38-41 (print date-time, `Starting...`)
- line 44 (set `BASE_DIR` path to base directory)
- line 51 (Base image template path set up `UBUNTU_IMAGE`)
- line 57 (set up `VDI_FILE`)
- line 65-70 (set up Spark Workers)
- line 80 (set up `LOCAL_NETWORK_NAME`)
- line 88-141 (set up and provision VMs)
  - `Setting up worker`
  - `Creating Worker VM...`
  - `Modifying Worker Networking...`
  - `Creating Worker Storage Device...`
  - `Attaching Worker Storage...`
  - `Adjusting storage registration string.`
  - `Configuring CPUs...`
  - `Starting Remote Desktop services...`
  - `Setting up port forwarding...`
  - `SSH Port Number`
  
- line 143-144 (print `Starting VMs...`)
- line 154 (reset starting range)
- line 156-172 (start VMs after provisioning)
  - `Launching VM Worker`
  - `Setting up VRDE port forwarding...`
  - `Starting Worker VM...`
  - `VRDE Port Number`
- line 176-178 (print `Done.`)
