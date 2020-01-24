# create-spark_worker_node.sh

latest comment from original repo:
```
Virtual Machines Trial

#   OBJECTIVE:
#	The purpose of this script is to create the base image for a VM.
```
- line 31-34 (print date and time, `Starting...`)
- line 37 (set path to base directory `BASE_DIR`)
- line 44 (set path to base image template)
- line 51 (set up localhost network `LOCAL_NETWORK_NAME`)
- line 59-64 (set up spark worker)

- line 69-111 (deploy spark worker)
  - `Creating Worker VM...`
  - `Modifying Worker VM...`
  - `Creating Worker HD...`
  - `Creating Worker Storage...`
  - `Attaching Worker Storage...`
  - `Attaching Image to Worker Storage...`
  - `Configuring CPUs...`
  - `Starting Remote Desktop services...`
  - `Setting up port forwarding...`
  - `Deploying Worker VM...`

- line 114-116 (print `Done.`)
