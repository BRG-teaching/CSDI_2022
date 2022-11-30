# RV2 plug-in

## About RV2

RV2 is a heavily documented plug-in for Rhino developed by the Block Research group which is consistenly updated and is constantly growing in scope. 

The online documentation for RV2 [can be found at this link](https://blockresearchgroup.gitbook.io/rv2/).

The background code for RV2 lives in the Github Repository [which is located here](https://github.com/BlockResearchGroup/compas-RV2).


## Preparation

Open Rhino and run the command `EditPythonScript` in the Rhino command prompt or from the toolbar: `Tools > PythonScript > Edit`. Afterwards, you can simply close Rhino.

## Installation

The installation process for RV2 is just updating the environment which we created during the install of IGS. On Mac, open the **Terminal app**. On Windows, use the **Anaconda Prompt**. If you need a reminder on how to do this, please take a look at the IGS install steps.

Next, run this line:


'''
conda env update -f https://blockresearchgroup.github.io/compas-IGS2/environment.yml
'''

After updating is finished, repeat [3. Installing the Plug-ins in Rhino](igs-plug-in.md#3.-installing-the-plug-ins-in-rhino). Then, go through the steps for [Loading the Toolbars](igs-plug-in.md#loading-the-toolbars) but instead of checking `IGS` check `RV2`.

That should be the end of the installation process! If you run into any issues, please post them with screenshots in the slack channel.