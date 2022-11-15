
## Conda Environemnts

### 1. Create conda environment

(i) Create an empty environment

    conda create --name {env_name}

(ii) Create an environment + specific python version

    conda create --name mlenv python==3.7.5

(iii) Create an environment + specific Python version + packages

    conda create --name env_name python==3.7.5 package_name1 package_name2

### 2. Activate the environment

- conda activate {env_name}
- To deactivate whichever you are currently in, use:

      conda deactivate

### 3. Install more packages

- install multiple packages from requirements.txt :

      pip install -r requirements.txt

### 4. See the list of packages and environments

- Show list of packages in current environment
  - conda list
- See list of packages in specific environment

      conda list -n myenv
- See list of environments

      conda env list

###### or

    conda info --envs

### 5. Remove an environment

    conda env remove -n env_name

### 6. Build an identical environment

To create an environment that is identical to an existing one, explicitly create a spec file of the environment you want to duplicate and use it at the time of creating the new env.

- Step 1: Create spec file

      conda list --explicit > spec-file.txt
- Step 2:
  
      conda create --name myenv --file spec-file.txt

You can do this in the same machine or a different machine as well, if you have the spec list.
If you want to install the packages in spec file, in an existing environment, run this.

    conda install --name env_name --file spec-file.txt

### 7. Sharing environments across platforms (better way)

There is a common problem when you try to replicate your environment in another system / platform.

When you create an environment and packages, lets say you run something like this (insert your package names.**

    conda install python=3.7 pkg_name1 pkg_name2 pkg_name3

This downloads and installs numerous other dependent packages in order to make the packages you wanted to install work.
This can easily introduce packages that may not be compatible across platforms.

So instead, use this:

    conda env export --from-history > environment.yml

Adding --from-history flag will install only the packages you asked for using conda. It will NOT include the dependency packages or packages you installed using any other method.

Now, How to re-create the environment?

Pass the environment.yml and the other person can re-create your environment by running:

    conda env create -f environment.yml

### 8. Restore / Rollback to an earlier version of an environment

Conda maintains a history of changes you make to an environment, by changes, I mean the changes you made using the conda commands. It allows you to roll back changes by using revision numbers.

Upon activating an environment, first see the revisions and the revision numbers using this.

    conda list --revisions
Then, roll back
    
    conda install --rev 3

source : [https://www.machinelearningplus.com/deployment/conda-create-environment-and-everything-you-need-to-know-to-manage-conda-virtual-environment/]
