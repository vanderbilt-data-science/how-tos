# How to Create a Conda Virtual Environment on ACCRE from a Remote Repository with YML file

This file will detail how you can create your own virtual environment (VE) on ACCRE from a remote repository with `yml` file governing the required packages, and then use it through the [ACCRE Portal](https://portal.accre.vanderbilt.edu).  The following steps assume that you already have an ACCRE account and are familiar with using the ACCRE portal for Jupyter notebooks, as well as the user interfaces for the programs that you will use herein.  In this is unfamiliar to you or you do not have an ACCRE account, please consult the `accre-basic-howto` [how-to](https://github.com/vanderbilt-data-science/how-tos/tree/master/accre-basic-howto) in this repository _first_.

## Accessing ACCRE for computing
Using your VUNetID and ACCRE password, log onto ACCRE via the [ACCRE portal](https://portal.accre.vanderbilt.edu). Navigate to the top menu and click on `Clusters` and select `>_ACCRE C7 Shell Access`. A new tab will open, and may ask for your ACCRE password.  You're now logged onto a shared gateway to the cluster.  This is where you'll create your VE for use with your Jupyter notebook.

## Loading Anaconda
As you likely know, Anaconda is a software ecosystem which simplifies a number of efforts in executing data science projects, including package management.  We first need to load Anaconda on the cluster.  To do this, type `module spider Anaconda`.  Identify the name/version of Anaconda you wish to load, e.g., `Anaconda3/2019.10`, and type `module load Anaconda3/2019.10`.  This loads Anaconda packages and conda package management capabilities onto ACCRE.

## Cloning the remote repo
Now, you'll clone the remote repo into your directory of interest.  To identify where you are in your home directory now, type `pwd` to print the working directory.  You can use `ls` to identify all of the contained directories in case you want to `cd` (change your directory, e.g., `cd child_directory`) into one of these other directories.  Now that you're in your directory of interest, use `git clone <remote-repository>` to clone your repository.  For example, `git clone https://github.com/vanderbilt-data-science/how-tos`.  This will create a clone of your repo from the remote server.

## Create conda VE
Now, we create the conda VE from the contained yaml file.  First, we will `cd` into our repo (e.g., `cd how-tos` will get us into the repo we cloned in the step [above](#cloning-the-remote-repo)).  Type `ls` and inspect the contents to ensure that there is a file with a file type `.yml`.  Note the name; here, we will assume that it is `environment.yml`.

To create the VE from this yml file, we'll type `conda env create -f environment.yml`.  When prompted to accept the packages, type `y` and click enter.  The packages will install; don't worry, this may and likely will take a while.  Go grab a cup of coffee or take your dog on a walk.

After your installation is complete, inspect the last few lines of the install.  They should contain information about the name of the environment and the commands necesary to activate it.  Alternately, type `head -1 environment.yml` (assuming `environment.yml` is the name of your environment file).  The name of the environment will be listed here in the form: `name: env_name`.  Mentally note the exact name and representation of the environment name.

## Create Jupyter notebook in environment
Now, head back over to your other ACCRE dashboard tab.  If you've accidentally closed it, just navigate back to [ACCRE portal](https://portal.accre.vanderbilt.edu).  Go to the top menu and click on `Interactive Apps`.  From the dropdown menu, choose `Jupter notebook (GPU)`.  Make sure you choose this **GPU** option.  If your DSI collaborator has shared with you the number and type of settings for your Jupyter notebook, use their estimates.  Otherwise, you may use the defaults here or customize according to your needs:

- **GPU Enabled Slurm Account**: `p_dsi_acc`
- **Number of hours**: `4`
- **Number of requested GPU resources**: `1`
- **GPU Architecture**: `Pascal`
- **Working directory**: `${ACCRE_RUNTIME_DIR}`
- **Python version**: `Python 3.6.3 / Anaconda 5.0.1`
- **Use a virtual environment checkbox**: `uncheck`
- **Python or Conda Virtual Environment**: `leave blank`