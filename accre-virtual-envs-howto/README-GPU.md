# How to Create a Virtual Environment on ACCRE for your **GPU** Computing Environment

This file will detail how to create a virtual environment on ACCRE for GPU computing.  Note that the following steps assume that you already have an ACCRE account and are familiar with using the ACCRE portal for Jupyter notebooks, as well as the user interfaces for the programs that you will use herein.  If this is unfamiliar to you or you do not have an ACCRE account, please do the `accre-basic-howto` how-to in this repository *first*.

## Accessing ACCRE for GPU computing
Using your VUNetID and password, log onto ACCRE via the [ACCRE portal](https://portal.accre.vanderbilt.edu).  Navigate to the top menu and click on `Interactive Apps`.  From the dropdown menu, choose `Jupter notebook (GPU)`.  Make sure you choose this **GPU** option.  If the collaborator has shared with you the number and type of settings, use their estimates.  Otherwise, you may use the defaults here or customize according to your needs:

- **GPU Enabled Slurm Account**: `p_dsi_acc`
- **Number of hours**: `4`
- **Number of requested GPU resources**:" `1`
- **GPU Architecture**: `Pascal`
- **Working directory**: `${ACCRE_RUNTIME_DIR}`
- **Python version**: `Python 3.6.3 / Anaconda 5.0.1`
- **Use a virtual environment checkbox**: `uncheck`
- **Python or Conda Virtual Environment**: `leave blank`

Now that you've made your options for your Jupyter work environment click `Launch`.  This will lead you to another page where ACCRE's scheduler (called SLURM) will try to schedule the time and resources you requested in your notebook.  It will go from a `Queued` state to a `Starting` state and finally be ready when the `Connect to Jupyter` button appears.  Click this button when it appears.

## Creating the virtual environment
Now, you will create a virtual environment.  The reason you want to create a virtual environment is because sometimes, some packages don't "play nice" together and require upgrading/downgrading packages that other packages you've installed might depend on.
