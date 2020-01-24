# soft_launch_master.sh
latest commit comment from original repository:
```
Master Node launch.

#   OBJECTIVE:
#	The purpose of this script is to start the Spark Master VM after it has been created.  The 'deploy' script creates
#	the VMs from scratch and launches them after, but this script just starts them after they have been created.
```
- line 32-35 (print `Starting Spark Master...`)
- line 38 (set `BASE_DIR`)
- line 43, 44 (set `SPARK_MASTER_NAME`, `SPARK_MASTER_VRDE_PORT`)
- line 46 (execute job in the background)
- line 49-51 (print `Done`.)
