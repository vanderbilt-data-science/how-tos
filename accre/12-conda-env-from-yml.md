# How to Create a Conda Virtual Environment on ACCRE from a Remote Repository with YML file

This file will detail how you can create your own virtual environment (VE) on ACCRE from a remote repository with `yml` file governing the required packages, and then use it through the [ACCRE Portal](https://portal.accre.vanderbilt.edu).  The following steps assume that you already have an ACCRE account and are familiar with using the ACCRE portal for Jupyter notebooks, as well as the user interfaces for the programs that you will use herein.  In this is unfamiliar to you or you do not have an ACCRE account, please consult the `10-accre-jupyter-101` [how-to](https://github.com/vanderbilt-data-science/how-tos/tree/master/accre) in this repository _first_.

## Accessing ACCRE for computing
Using your VUNetID and ACCRE password, log onto ACCRE via the [ACCRE portal](https://portal.accre.vanderbilt.edu). Navigate to the top menu and click on `Interactive Apps`.  From the dropdown menu, choose `Jupter notebook (GPU)`.  Make sure you choose this **GPU** option.  If your DSI collaborator has shared with you the number and type of settings for your Jupyter notebook, use their estimates.  Keep in mind that Anaconda installs packages and dependencies according to the ACCRE GPU architecture that you choose.  Otherwise, you may use the defaults here or customize according to your needs:

- **GPU Enabled Slurm Account**: `p_dsi_acc`
- **Number of hours**: `4`
- **Number of requested GPU resources**: `1`
- **GPU Architecture**: `Turing`
- **Working directory**: `leave blank`
- **Python version**: `Python 3.6.3 / Anaconda 5.0.1`
- **Use a virtual environment checkbox**: `uncheck`
- **Python or Conda Virtual Environment**: `leave blank`

Now that you've made your options for your Jupyter work environment click `Launch`.  This will lead you to another page where ACCRE's scheduler (called SLURM) will try to schedule the time and resources you requested in your notebook.  It will go from a `Queued` state to a `Starting` state and finally be ready when the `Connect to Jupyter` button appears.  Click this button when it appears.

## Cloning the remote repo
Now, you will create your VE in your home directory on ACCRE's filesystem.  Open up a terminal in Jupyter by going to the upper right hand side of your screen and clicking the `New` button, and select `Terminal` from the drop-down menu that appears.  In the terminal, type `pwd` to view your current directory.  Ensure it is something of the form `/home/my_vunetid`.  
 
 Now, you'll clone the remote repo into your directory of interest.  You can use `ls` to identify all of the contained directories in case you want to `cd` (change your directory, e.g., `cd child_directory`) into one of these other directories.  Now that you're in your directory of interest, use `git clone <remote-repository>` to clone your repository.  For example, `git clone https://github.com/vanderbilt-data-science/how-tos`.  This will create a clone of your repo from the remote server.

## Create conda VE
Now, we create the conda VE from the contained yaml file.  First, we will `cd` into our repo (e.g., `cd how-tos` will get us into the repo we cloned in the step [above](#cloning-the-remote-repo)).  Type `ls` and inspect the contents to ensure that there is a file with a file type `.yml`.  Note the name; here, we will assume that it is `environment.yml`.

To create the VE from this yml file, we'll type `conda env create -f environment.yml`.  When prompted to accept the packages, type `y` and click enter.  The packages will install; don't worry, this may and likely will take a while.  Go grab a cup of coffee or take your dog on a walk.

After your installation is complete, inspect the last few lines of the install.  They should contain information about the name of the environment and the commands necesary to activate it.  Alternately, type `head -1 environment.yml` (assuming `environment.yml` is the name of your environment file).  The name of the environment will be listed here in the form: `name: env_name`.  Mentally note the exact name and representation of the environment name.

## Using your VE
Although you have created your VE, ACCRE requires that your VE be activated *before* you open your Jupyter notebook (i.e., when you're requesting resources through the ACCRE portal). Thus, if you have just followed the above instructions, go back to the tab where you clicked `Connect to Jupyter`.  Click the red `Delete` button on your instance.  If you accidentally closed this tab, simply go back to the [ACCRE portal](https://portal.accre.vanderbilt.edu) and click `Interactive Sessions`.  Click the red `Delete` button.

Now, you will create a new instance of a Jupyter notebook in which you will do your work.  Again, click `Interactive Apps` at the top of the screen.  Select `Jupyter notebook (GPU)`.  Now, enter your desired parameters for the work; again, you can use the defaults as above **WITH TWO ESSENTIAL CHANGES**.  **ENSURE** that you change the following fields:

- **Use a virtual environment checkbox**: `CHECK`
- **Python or Conda Virtual Environment**: `env_name`

Note that you will change `env_name` to the name of the VE that you created.  If you think you'll have a lot of interaction with the filesystem (lots of loading, saving, opening and closing of files, e.g., fast.ai), also use the following setting:

- **Working directory**: `${ACCRE_RUNTIME_DIR}`

Now, click `Launch` to submit your request to SLURM and `Connect to Jupyter` when your resources are available.

Open the `Terminal` from the `New` dropdown menu. The first line in parentheses should be the name of your selected VE.

## Likely following workflow
After creating your VE, now you likely want to run Jupyter notebooks in it using the GPU resources (see `accre-basic-howtos` in this repository for more details).  To do this, type `pwd` in the Terminal associated with your Jupyter notebook.  You should see your ACCRE home directory.  How you choose to work from here depends on how much communication will be required between a filesystem and your compute node.

If you load/save large files repeatedly or open and close a lot of files, you may want to choose to clone your repo locally and work on the local memory system of the GPU node.  To do this, you must have selected `${ACCRE_RUNTIME_DIR}` for your selections above for the Jupyter notebook.  Type `cd $ACCRE_RUNTIME_DIR` in your terminal.  This changes your directory to where the GPU local memory is stored.  Now, use `git clone` to clone your repository in the GPU local memory.  If you choose this route, make sure at the end of your work period to push all of your code changes up to GitHub or your remote repository.  Any work that isn't pushed will be deleted when your session ends.  You can delete the repo saved on your home directory, unless you need it for some other reason.

If this is not required, use your home directory and repo as usual.

Have fun!