# Project to setup and run AlphaFold on Nautilus cluster
## Create PVC
The first step is to create the PVC where we will store the data. This only needs to be done once in every namespace.
<br>
kubectl apply -f pvc-alphafold-data.yaml
<br>
## Download data to PVC
TBD - initial implementation, we mounted the PVC in a pod and ran the download steps manually. This is to download all the reference data into the PVC
## Run AlphaFold example
kubectl apply -f alphafold_gpu_monomer.yaml
In this example we copy over the bfd index files to the node local scratch as this needs to be fast access. Rest of the files remain in the PVC. After that we use the run_alphafold.sh script that is part of the docker container to run the alphafold example. The input was already staged in the PVC as well (eventually we could dynamically download this in the run itself).
