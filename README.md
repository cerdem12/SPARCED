# SPARCED-nf: A Nextflow Pipeline for SPARCED

SPARCED-nf is a Nextflow pipeline designed to be a more scalable and user-friendly version of the SPARCED model (previously the mechanistic pan-cancer signaling model) by the Birtwistle Lab. With minimal set-up, a user can configure the model for high-intensity runs on a Kubernetes cluster, or small-scale experiments on their local machine. More information on the model itself can be found [here](https://github.com/birtwistlelab/SPARCED)


## Dependencies

[Nextflow](https://www.nextflow.io/docs/latest/getstarted.html)
[Docker](https://docs.docker.com/get-docker/)

## Instructions to run locally
1. Clone this repository
2. Make sure the dependencies listed above are installed
3. Edit the files in the `input_data` folder as needed. These values will be built into the *creation* of the model. For editing the values present for the model's *simulation*, see the directions accompanying the next step.
4. Edit the `local-nextflow.config` file located in the `configs` folder. (for help, see [here](www.placeholder.com))
5. Navigate to the base directory of this project, and run the workflow with `nextflow kuberun . -c configs/local-nextflow.config`

## Instructions to run with Kubernetes
1. Clone this repository
2. Make sure the dependencies listed above are installed
3. Ensure you have a Kubernetes `config` file for your chosen cluster located in your `~/.kube` folder
4. Edit the files in the `input_data` folder as needed. These values will be built into the *creation* of the model. For editing the values present for the model's *simulation*, see the directions accompanying the next step.
5. Use `./kube-scripts/kube-load.sh <pvc-name> input_data` to load your input data to the PVC of the kube cluster
6. Edit the `kube-nextflow.config` file located in the `configs` folder. (for help, see [here](www.placeholder.com))
8. Run from the command line with `nextflow kuberun . -C nextflow.config`
9. After the run is finished, save your data from the PVC down to your laptop with `./kube-scripts/kube-save.sh <pvc-name> <work-directory>` (this `work directory` path is relative to your `workspace/$USER` directory in the PVC. So with the default configurations, it should just be `work`)

## Debugging
1. kube-uncorrupt


## Containerized requirements
sudo apt install libatlas-base-dev
sudo apt-get install libhdf5-serial-dev
sudo apt-get install swig
pip3 install requirements.txt


## Acknowledgements:

This work is a product of [Birtwistle Lab](http://www.birtwistlelab.com/) and multiple colloborators, including [Feltus Lab](https://www.clemson.edu/science/departments/genetics-biochemistry/people/profiles/ffeltus), [Hasenauer Lab](https://www.mathematics-and-life-sciences.uni-bonn.de/en/group-members/jan-hasenauer), and [Robert Blake](https://bbs.llnl.gov/RobertBlake.html) from LLNL.



## The Acronym:
The acronym SPARCED is composed of following elements, based on the sub-models in the mechanistic ODE model.

### S: SBML

### P: Proliferation

### A: Apoptosis

###  R: Receptor

###  C: Cell Cycle

###  E: Expression

###  D: Death
