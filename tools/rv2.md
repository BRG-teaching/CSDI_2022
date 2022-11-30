# RV2 plug-in

## About RV2

RV2 is a heavily documented plug-in for Rhino developed by the Block Research group which is consistenly updated and is constantly growing in scope. 

The online documentation for RV2 [can be found at this link](https://blockresearchgroup.gitbook.io/rv2/).

The background code for RV2 lives in the Github Repository [which is located here](https://github.com/BlockResearchGroup/compas-RV2).


## Installation

The installation process for RV2 involves updating the environment which we created during the install of IGS. On Mac, open the **Terminal app**. On Windows, use the **Anaconda Prompt**. If you need a reminder on how to do this, please take a look at the IGS install steps.

Next, run this line of code:


```
conda env update -f https://blockresearchgroup.github.io/compas-RV3/environment.yml
```

After updating is finished, repeat [3. Installing the Plug-ins in Rhino](igs-plug-in.md#3.-installing-the-plug-ins-in-rhino). Then, follow all the steps from [Loading the Toolbars](igs-plug-in.md#loading-the-toolbars) but instead of typing `IGS2__toolbar` in the Rhino command line, type `IGS2__toolbar`.

That should be the end of the installation process! If you run into any issues, please post them with screenshots in the slack channel.