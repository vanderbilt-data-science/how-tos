# how-tos

This repository contains code snippets, documentation, and details on how to perform tasks of interest.  The audience of the different how-tos will vary, so feel free to use/tailor the instructions to your familiarity level.

## How-to's available
1. `accre-basic-howto`: this how-to details how to obtain an ACCRE account, access the portal for Jupyter notebooks on ACCRE, clone a project repository onto ACCRE, and run cells in the Jupyter notebook
2. `accre-virtual-envs-howto` (soon): this how-to details how to create and use your own custom virtual environment on ACCRE

## Installation
To work with this repository and the collections of how-tos herein, you will most likely want to install *at least* Git to clone and work with the code in this repository.  Further instructions will be found in the `readme.md` file of the subdirectory for your selected how-to.

### Git
Git provides version control and facilitates collaboration between project contributors.  You will use git for one or more of these purposes:
1. Version control for your own projects
2. Version control for projects with multiple members
3. Cloning/forking repositories (obtaining a copy of the repository)
4. Syncing the local and remote repository

You can install Git from [here](https://git-scm.com/downloads) for your operating system.  For Mac OSX, you may need to install the XCode Commnand Line tools.  This can be done by typing `git --version` in your terminal.  If git is not installed, this should prompt you to install XCode tools.

### Repo download (Optional)
**Note**: You may or may not need to clone this repository to follow your desired how-to.  Additionally, it may be difficult to read the readme file without the rendering that GitHub provides.  A good workflow is to have the how-to readme via GitHub open in one tab, and follow the installation instructions (e.g., cloning this repository) indicated by this how-to readme in other browser tabs or programs if necessary.

To locally clone this repo:
1. Scroll up and click the bright green `Clone or download` button.  
2. Click the clipboard next to the URL of the repository.  This will copy the repository link.
3. Determine the directory where you want your repository to be located (e.g., Documents\projects)
4. Right click and click the option `Git Bash here`.
5. The Git Bash screen appears and should look like a terminal.  Type `pwd` and press enter.  Ensure that the directory stated is where you want your project.  Otherwise, close Git Bash and return to step 3.
6.  Type 'git clone ' and then right-click so that a drop down menu appears.  Click paste.  Your total command should be something like:
```
git clone https://github.com/vanderbilt-data-science/how-tos
```
Press enter.

Congratulations, you've cloned the repository.  This is your first step.  Now, open your file explorer and navigate to your new folder.  After you click on it, find the subdirectory for your how-to.  Follow the steps in the readme file to perform your desired task.
