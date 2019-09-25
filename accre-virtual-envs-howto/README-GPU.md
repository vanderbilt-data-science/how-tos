# How to Create a Virtual Environment on ACCRE for your **GPU** Computing Environment

This file will detail how to create a virtual environment (VE) on ACCRE for GPU computing.  Note that the following steps assume that you already have an ACCRE account and are familiar with using the ACCRE portal for Jupyter notebooks, as well as the user interfaces for the programs that you will use herein.  If this is unfamiliar to you or you do not have an ACCRE account, please do the `accre-basic-howto` how-to in this repository *first*.

## Accessing ACCRE for GPU computing
Using your VUNetID and password, log onto ACCRE via the [ACCRE portal](https://portal.accre.vanderbilt.edu).  Navigate to the top menu and click on `Interactive Apps`.  From the dropdown menu, choose `Jupter notebook (GPU)`.  Make sure you choose this **GPU** option.  If your DSI collaborator has shared with you the number and type of settings for your Jupyter notebook, use their estimates.  Otherwise, you may use the defaults here or customize according to your needs:

- **GPU Enabled Slurm Account**: `p_dsi_acc`
- **Number of hours**: `4`
- **Number of requested GPU resources**: `1`
- **GPU Architecture**: `Pascal`
- **Working directory**: `${ACCRE_RUNTIME_DIR}`
- **Python version**: `Python 3.6.3 / Anaconda 5.0.1`
- **Use a virtual environment checkbox**: `uncheck`
- **Python or Conda Virtual Environment**: `leave blank`

Now that you've made your options for your Jupyter work environment click `Launch`.  This will lead you to another page where ACCRE's scheduler (called SLURM) will try to schedule the time and resources you requested in your notebook.  It will go from a `Queued` state to a `Starting` state and finally be ready when the `Connect to Jupyter` button appears.  Click this button when it appears.

## Creating the VE
Now, you will create a VE.  The reason you may want to create a VE is because sometimes, packages don't "play nice" together.  For example, installing `Package 1` requires upgrading/downgrading package versions that `Package 2` you used in another project might depend on.  Now, `Package 2` might have unexpected behavior when you try to use it in your other project!

Creating separate environments (i.e., VEs) can assuage these types of issues for you.  To create one, open up a terminal in Jupyter by going to the upper right hand side of your screen and clicking the `New` button, and select `Terminal` from the drop-down menu that appears.  In the terminal, type `pwd` to view your current directory.  Ensure it is something of the form `/home/my_vunetid`.  Now, you will create your VE in your home directory on ACCRE's filesystem.  In the following code, we will create a VE called `test-env`, and we will install a package called `anaconda`.  You should substitute the name of your package(s) if you already know what packages you're interested in.  \**See notes about additional package installation [below](#installing-other-packages).

To do this, type the following:
```
conda create -n test-env anaconda
```
If you wanted to install several packages (e.g., we're installing `pandas`, `scikit-learn`, and `matplotlib` here) simultaneously while creating your VE (here called `ds-env`), you could write something of the form:
```
conda create -n ds-env pandas scikit-learn matplotlib
```
Either press `Enter` or `y` then `Enter` when the prompt appears asking you whether you want to install the packages it has listed.  The packages will begin to install.  Don't worry if the process appears to hang or seems to take a long time.  This can take 30+ minutes and appear to have no progress until it simply just finishes.  You can determine when it has finished when it gives you a notification about how to activate the VE and then shows the bash prompt.  Now, activate your created VE:
```
source activate test-env
```
As you can see, the name of your VE pops up in parentheses beside your bash prompt.  This indicates that you're using the indicated VE.  If you have any other packages to install, you can do this now.  For example, if we wanted to install `tensorflow-gpu`, we could type:
```
conda install tensorflow-gpu
```
Additionally, if you want to install a specific version of your package, you can modify the command in the following way:
```
conda install tensorflow-gpu=1.3
```
### Installing other packages

Also note that you may (and should) install your desired Conda packages in the creation of the VE (see Conda documentation [here](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) for more information).  For example, if you already knew you wanted to install the `tensorflow-gpu` package, version 1.3, with a VE named `tf-gpu`, you could enter:
```
conda create -n tf-gpu tensorflow-gpu=1.3
```
Another example is the fast.ai package, which requires installation from the fastai channel (indicated by the `-c` flag), which could be created as:
```
conda create -n fastai-env -c fastai fastai
```

## Using your VE
Although you have created (and activated) your VE, ACCRE requires that your VE be activated *before* you open your Jupyter notebook (i.e., when you're requesting resources through the ACCRE portal). Thus, if you have just followed the above instructions, go back to the tab where you clicked `Connect to Jupyter`.  Click the red `Delete` button on your instance.  If you accidentally closed this tab, simply go back to the [ACCRE portal](https://portal.accre.vanderbilt.edu) and click `Interactive Sessions`.  Click the red `Delete` button.

Now, you will create a new instance of a Jupyter notebook in which you will do your work.  Again, click `Interactive Apps` at the top of the screen.  Select `Jupyter notebook (GPU)`.  Now, enter your desired parameters for the work; again, you can use the defaults as above **WITH TWO ESSENTIAL CHANGES**.  **ENSURE** that you change the following fields:

- **Use a virtual environment checkbox**: `CHECK`
- **Python or Conda Virtual Environment**: `test-env`

Note that you will change `test-env` to the name of the VE that you created.  For example, to use our fast.ai VE, we would input `fastai-env` in that field.  Now, click `Launch` to submit your request to SLURM and `Connect to Jupyter` when your resources are available.

Open the `Terminal` from the `New` dropdown menu. The first line in parentheses should be the name of your selected VE.

## Likely following workflow
After creating your VE, now you likely want to run Jupyter notebooks in it using the GPU resources (see `accre-basic-howtos` in this repository for more details).  To do this, type `pwd` in the Terminal associated with your Jupyter notebook.  You should see your ACCRE home directory.  Now, type `cd $ACCRE_RUNTIME_DIR`.  This changes your directory to where the GPU local memory is stored.  Now, use `git clone` to clone your repository in the GPU local memory.
