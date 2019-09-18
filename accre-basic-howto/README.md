# README.md
This file will detail how to setup and access ACCRE and general Jupyter notebooks.  Start here.  To skip to the nitty-gritty, click [here](#accessing-accre).

## Introduction
Welcome to Jupyter notebooks and ACCRE!  Why do people use either of these things?

### Jupyter notebooks
Jupyter notebooks facilitate something which is called *literate programming*.  Literate programming allows you to quite nearly tell a story or narrate your thought process as you code.  Jupyter notebooks assist in this by providing a user interface (UI) which allows for mixing of different information types.  These different information types are housed in different cells, and allows intermixing of text with markup cells interspersed between code cells, which execute code.

The backend of the Jupyter notebook is a kernel, which allows for processing and computation of your code.  The kernel we will use here is a  Python kernel, although many others are available including R and Julia.  As you will notice, the Jupyter notebook interface runs through a browser, which provides a relatively ubiquitous interface to the underlying kernel.  Keep in mind that this isn't a web-based service; if you have secure data, no data moves from your computer to a remote server for processing.  Everything is done locally.

More information about Jupyter notebooks may be found [here](https://jupyter.org/).

### Advanced Computer Center for Research and Education (ACCRE)
ACCRE is a high performance cluster that services groups with high performance computing needs.  This usually comes in the form of highly computationally intensive programs, which may require large amounts of data combined with a high degree of computation.  ACCRE accelerates the research that requires this type of computing by curating and maintaining a cluster with associated storage, removing the expertise needed to create an architecture like this from the researcher.  ACCRE has both GPU and CPU computing nodes, and based on your project needs, you may use one, the other, or both.

## Accessing ACCRE
In order to use ACCRE, you will need to have an ACCRE account affliated with the Data Science Institute.  To obtain one of those, go [here](https://www.vanderbilt.edu/accre/getting-started/) and follow the outlined steps.  When filling out the form, make sure you make the following selections in the relevant fields:

- **Department**: `Data Science Institute`
- **School or Affiliation**: `Trans-Institutional Programs (e.g., Data Science Institute)`
- **Group**: `Data Science Institute (p_dsi)`

Notify your Vanderbilt collaborator when you do this to ensure that the PI (gives approval for you to be added to `p_dsi` group) is aware of your request.  Your request will take around 3-4 days to process, and you'll receive a temporary password to access ACCRE.  Follow the instructions in the email to reset your password to something reasonable for you.

Now that you have your ACCRE account, let's log onto ACCRE.  Visit the [ACCRE portal](https://portal.accre.vanderbilt.edu) and enter your VUNetID and **ACCRE** password.  This may (and should) be different than your VUNetID password.

Navigate to the top menu and click on `Interactive Apps`.  From the dropdown menu, choose `Jupyter notebook` or `Jupyter notebook (GPU)`.  The difference is that the first one uses CPU only, and the latter also uses GPUs.  The fields for the GPU and CPU form should be relatively similar.  If your collaborator has shared with you the number of resources, use their estimates.  Otherwise, you may use the defaults here:

### GPU Jupyter Default Options
**GPU Enabled Slurm Account**: `p_dsi_acc`
**Number of hours**: `4`
**Number of requested GPU resources**:" `1`
**GPU Architecture**: `Pascal`
**Working directory**: `${ACCRE_RUNTIME_DIR}`
**Python version**: `Python 3.6.3 / Anaconda 5.0.1`
**Use a virtual environment checkbox**: `uncheck`
**Python or Conda Virtual Environment**: `leave blank`

Ask your collaborator more about these settings.  For example, if using fast.ai, you may want to use a `Tesla` GPU architecture with the `Python/3.6.3 GCC/6.4.0-2.28` Python version in the virtual environment stored at `/labs/accre_public/pascal/fast.ai.v2`.  Ask them - they'll know!

### CPU Jupyter Default Options
**Number of hours**: `4`
**Maximum memory (GB)**: `4`
**Number of CPU cores**: `1`
**CPU Architecture**: `Any`
**Working Directory**: `Home`
**Python version**: `Python 3.6.3 / Anaconda 5.0.1`
**Use a virtual environment checkbox**: `uncheck`
**Python or Conda Virtual Environment**: `leave blank`

Make sure to ask your collaborator further about these options.

Now that you've made your options for your Jupyter work environment click `Launch`.  This will lead you to another page where ACCRE's scheduler (called SLURM) will try to schedule the time and resources you requested in your notebook.  It will go from a `Queued` state to a `Starting` state and finally be ready when the `Connect to Jupyter` button appears.  Click this button when it appears.

## Cloning a Repository via Jupyter notebooks
The user interface (UI) that you now see is the **Jupyter Dashboard**.  If you used the default options above for the GPU, you should see no files listed.  If you used the CPU option, you should see your home directory on the ACCRE filesystem.  It should be empty with the exception of a few automatically-generated files.

### GPU Users ONLY
f you're using the GPU, you have a few additional steps you may need to do before you clone the repository.  This is because you need to make sure you're using the GPU local memory and not your home directory on ACCRE's default filesystem.  This is a consequence of the "small file" problem; when writing small files across the type of filesystem that ACCRE has, this can cause your program to run exquisitely slowly.  You want to avoid this, and thus, we use `${ACCRE_RUNTIME_DIR}`, a variable which stores the location of the local GPU memory.  This is the location to which you will clone your repository.

To get to this location, look on the upper right hand side of the screen and click the `New` drop-down menu.  Click `Terminal`.  This will open up a bash terminal.

Type `pwd` and press enter.  If the shell returns something like `\home\my_vunetid`, then you need to now change the directory to your GPU's local memory.  To do this, type `cd $ACCRE_RUNTIME_DIR`.  You should see a change in your bash prompt from:
```
vunetid@gpu00xx ~]$
```
to something of the form:
```
vunetid@gpu00xx u38273648.e889866.989e]$
```
Now, you can type `pwd`.  It returns some garble of numbers and letters indicating that you're now accessing the local GPU memory.

### All Users
If you haven't already opened a terminal, you can do so from your Jupyter Dashboard.  At the upper right hand side of your screen, click the `New` drop-down menu.  Click `Terminal`.  This will open up a bash terminal.

Now, you're ready to clone your repository of interest to your current file storage.  This will be nearly identical to the local initial clone you did of this repository (if you performed this step; not necessary for this how-to).  If you don't have a target repository of interest yet, just clone this one.

To clone this repo:
1. Find your repository of interest via github.  If you're not cloning a specific repository for your project, you can try out one [here](https://github.com/vanderbilt-data-science/how-tos). On the right hand side of the screen, click the bright green `Clone or download` button.  
2. Click the clipboard next to the URL of the repository.  This will copy the repository link.
3. Navigate back to your ACCRE bash terminal.  Type 'git clone ' and then right-click so that a drop down menu appears.  Click paste (`Ctrl-V` works here as well).  Your total command should be something like:

```
git clone https://github.com/vanderbilt-data-science/how-tos
```
Press enter.

Congratulations, you've cloned the repository!

## Opening a Jupyter notebook
Now that you've cloned the repository onto your desired directory on ACCRE, you're ready to run a Jupyter notebook!  To do this, go back to your Jupyter notebook tab. As you can see, you have a new directory with the repository cloned!  The Jupyter Dashboard operates similarly to a regular file browser; click the directory you want to view its contents.  If you cloned the `how-tos` repository, click on the `accre-basic-howto` folder.  Inside of it, you should see this readme (`README.md`) and a Jupyter notebook (`accre-basic-howto.ipynb`).  Click on the Jupyter notebook to open it.  Congratulations!  You've opened a Jupyter notebook and are ready to start running code.  Follow the instructions there!

## When you're finished
When you're finished running your Jupyter notebook, **MAKE SURE YOU DELETE THE INSTANCE OF JUPYTER FROM ACCRE**.  You can do this by going to the tab where you clicked `Connect to Jupyter`.  Click the red `delete` button on your instance.  

If you've accidentally closed this tab, simply go back to the [ACCRE Portal](https://portal.accre.vanderbilt.edu), and click `Interactive Sessions`.  This will show you a list of the current resources of ACCRE you are currently consuming.  Click the red `Delete` button on your instance.  This will release the resources of the cluster back to others who may need to use it.  Recall that ACCRE is a shared computing resource; make sure you always use it responsibly.

