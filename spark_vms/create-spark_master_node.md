# create-spark_master_node.sh

latest commit from original repository:
```
#   OBJECTIVE:
#	The purpose of this script is to deploy a set of Virtual Machines (VMs) that will collectively act as a Spark
#	cluster.  The overall idea is to deploy an odd number of nodes that collectively form the Spark cluster. The
#	reason for the odd number is that one node will be the 'Master' node, and the remaining n-1 nodes will be the
#	workers (Spark Executors).
#
#	This script launches onde VM that will act as the Master node.
```

- line 36-39 (print date and `Starting...`)
- line 42 (set `BASE_DIR`, path to base directory)
- line 49 (direct path to base image template)
- line 56-60 (`set up 'localhost' network that nodes will use to communicate`)
- line 67-72 (set up Master node)
- line 77-138 (deploying master node)
  - `Creating Master VM...`
  - `Modifying Master VM...`
  - `Creating Master HD...`
  - `Attaching Master Storage...`
  - `Attaching Image to Master Storage...`
  - `Configuring CPUs...`
  - `Starting Remote Desktop services...`
  - `Setting up SSH port forwarding...`
  - `Setting up Hadoop port forwarding...`
  - `Setting up Ganglia port forwarding...`
  - `Setting up Apache port forwarding...`
  - `Setting up Spark port forwarding...`
  - `Setting up VRDE port forwarding...`
  - `Deploying Master VM...`
  
  - line 142-144 (`Done.`)
