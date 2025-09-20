# Automatically building scientific research environment
<div style="text-align: justify"> For many novices who are just beginning in bioinformatics, it is a headache to explore the installation environment of different software. CONDA can create different virtual environments and install them into different virtual environments according to different software, which is not easy to conflicts due to the dependencies of different programs. It only needs to call different virtual CONDA environments to call different software. This method can use in linux and mac os.</div>
<div style="text-align: justify"> <br> </div>
Create a new virtual environment under the specified directory, and enter the command:

```
# Python 
conda create --prefix=./conda_work/envs/python3 python=3.8
conda create --prefix=./conda_work/envs/python2 python=2.7

# amber 
conda create --prefix=./conda_work/envs/amber  --no-default-packages
conda activate amber
conda install -c conda-forge ambertools

# gromacs
conda create --prefix=./conda_work/envs/gromacs --no-default-package
conda activate gromacs
conda install -c conda-forge -c bioconda gromacs

# R
conda create -n R3.5
source activate R3.5
conda install r-base=3.5.1
## R packages usually need to start with r-
conda install r-ggplot2
## If it cannot be found, you can use this command to search the corresponding R package. Anaconda here is the path of the original CONDA, not in r3.5 environment
anaconda search -t conda r-ggplot2
## Show Chanel of this package
anaconda show BioBuilds/r-ggplot2
## Install according to Anaconda show
conda install --channel https://conda.anaconda.org/BioBuilds r-ggplot2

# Openbabel 
conda install -c openbabel openbabel (Note: Environment requiring Python 2.7)
conda install -c conda-forge openbabel (Note: Attention: Requires an environment after Python 3.0）
```

Use the command to view the currently owned virtual environment:
```
conda info --envs
```

Set the shortcut opening method for each virtual environment and write the following lines into the environment file (Linux: ~/.bashrc MACOS: ~/.zshrc).

```
alias work="conda activate ../python3"
alias py2="conda activate ../python2"
alias amber="conda activate ../amber"
alias gromacs="conda activate ../gromacs"
```
Note: The path (../python3) should be a full path.

Delete virtual environment:

Input for example:
```
conda remove --name en_name --all
```
<div style="text-align: justify"> In the last, it is worth noting that if you want to use multiple software in the same virtual environment, and the software will call each other, you need to deploy multiple software in the same environment. For example, when using Jupiter notebook, Python and R, other situations will not be listed one by one.</div>
<div style="text-align: justify"> <br> </div>
