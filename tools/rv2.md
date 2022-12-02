# RV3 plug-in

## About RV3

RV2 is a heavily documented plug-in for Rhino developed by the Block Research group which is consistenly updated and is constantly growing in scope.

The online documentation for (old) RV2 [can be found at this link](https://blockresearchgroup.gitbook.io/rv2/).

The background code for (old) RV2 lives in the Github Repository [which is located here](https://github.com/BlockResearchGroup/compas-RV2).

## Installation

The installation process for RV3 involves updating the environment which we created during the install of IGS. On Mac, open the **Terminal app**. On Windows, use the **Anaconda Prompt** (**not** the powershell) and run as . If you need a reminder on how to do this, please take a look at the IGS install steps.

Next, run these two lines of code (makes sure you are **not** in your `csd1` environment):

```
conda env update -f https://blockresearchgroup.github.io/compas-RV3/environment.yml
```

After updating is finished, **make sure Rhino is not running** then run these lines of code:

```
conda activate csd1
```

```
python -m compas_rhino.install -v 7.0
```

Open Rhino and as before type `EditPythonScript`. Once the window has popped up, close down your Rhino. This just makes sure that Rhino sees your latest changes. Open Rhino and type `COMPAS__toolbar`, then `RV3_toolbar` .

On the COMPAS toolbar, click the button with the cloud with a red arrow. This will refresh your connection to the server.

This ends the installation process! If you run into any issues, please post them with screenshots in the slack channel.
