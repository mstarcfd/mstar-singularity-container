
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
- `--app solver` : Calls the solver

Run:

    singularity run --nv --app solver ../mstar.sif



