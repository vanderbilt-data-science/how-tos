# How to Connect a Jupyter Console to a Locally Running Notebook Kernel

As you know, investigating the values of variables in a Jupyter notebook requires using `print` statements or dedicating the last line of the cell to output and show your variable of interest.  Instead of inserting these `print` or output lines and then erasing them later or as you go, you can use a console connected to your notebook to show variables without such excess code being in-line with your functional code.  Here's how!

1. In your existing notebook, choose or create an empty code cell (e.g., from within a cell press the `Esc` key until the cell side bar turns blue, and then type `a`)
2. In this new code cell, type `%connect_info`.  At the time of writing, the rest of the steps are right there in the output of this cell!  But, we'll outline them specifically here.
3. Navigate back to the Dashboard (main Jupyter page with the files and directories listed) and click on the `New` button on the right hand side of the page.  Choose `Terminal`.
4.  If this notebook is the most recent notebook you've created (i.e., you haven't opened any notebooks after your notebook of interest), connecting a console is simple!  Type `jupyter console --existing` into the terminal.  An IPython interpreter should now start in your terminal.  Try typing in one of your notebook variables to view its value.
5.  If this notebook isn't the most recent notebook you've created, you'll need to look more at the output of the `%connect_info` cell.  In the 2nd to last `$>` line, you should see a command of the format : `jupyter <app> --existing kernel-*.json`, where `*` is a string of numbers and letters separated by dashes.  This command is how you connect any compatible app of interest to this kernel, referenced by the `kernel-*.json` file.  Thus, to connect the console app to the kernel, copy this line and paste it in the console.  Before pressing enter, change the `<app>` parameter to `console`.  An IPython interpreter should now start in your terminal.  Try typing in one of your notebook variables to view its value.

Happy coding!
