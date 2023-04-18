
# M-Star CFD Singularity Container

This docker image can run the following M-Star components:

- M-Star CFD Python Pre API
- M-Star CFD Solver

Requirements:

- M-Star license (floating or node-locked)
- Singularity

## Build the image

    sudo singularity build mstar.sif mstar.def

## Run the image

Setup your license environment variable if not already set

    export mstar_LICENSE=5053@mylicenseserver

Create an example case. Creates a new directory called `CASE`
    
    singularity run mstar.sif python3.9 create_test.py

Run the example. Note the usage of the parameters:

- `--nv` : Invokes Nvidia driver initialization
- `--app solver` : Helper alias to call the solver quickly. Removes existing results in `out/` directory, uses all GPUs, and writes log file. 

Run:

    singularity run --nv --app solver ../mstar.sif


Or call with the solver command line:

    singularity run --nv  ../mstar.sif mstar-cfd-mgpu -i input.xml -o out --gpu-auto
