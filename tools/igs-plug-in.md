# Algebraic GS Plug-in

{% hint style="danger" %}
To install the plug-in for Algebraic GS, please make sure that you have installed [Anaconda 3](anaconda.md).&#x20;
{% endhint %}

## Preparation

If you have a fresh installation of Rhino, or if you have never used it for scripting with Python, please open the software and launch the Python Script Editor. This will create a bunch of folders that are otherwise not yet available and are needed for the installation process of COMPAS in Rhino. You can launch the Python Script Editor in Rhino by typing the command `EditPythonScript` in the Rhino command prompt or from the toolbar: `Tools > PythonScript > Edit`. You don't need to do anything else. Afterward, you can close Rhino again.

## Installation

The installation process involves commands that have to be executed on the command line. **On Mac**, you can use the _**Terminal**_ app. **On Windows**, you need to use the _**Anaconda Prompt**_ instead of the standard _Command Prompt_. The Anaconda Prompt is automatically installed when you install Anaconda.

<figure><img src="../.gitbook/assets/Anaconda Prompt.jpg" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Windows users may have to run the Anaconda Prompt "**as administrator**" to have sufficient permissions to execute all the commands successfully.
{% endhint %}

Now, you have to execute the following 3 commands **one after another**. To do that, copy the first command line in your Terminal / Anaconda Prompt and press `return/enter` .**This will take a few minutes to be executed so please be patient**. Once it finishes completely, execute the second command line. And, once the second is finished, execute the last one.

### 1. Creating an Environment and Downloading the packages

```
conda env create -f https://blockresearchgroup.github.io/compas-IGS2/environment.yml
```

### 2. Activating the Environment

```
conda activate csd1
```

### 3. Installing the Plug-ins in Rhino

{% hint style="warning" %}
Close all the Rhino windows you have opened. If you are using **Rhino 7.0**, please execute the following command.
{% endhint %}

```
python -m compas_rhino.install -v 7.0 --clean
```

Alternatively, if you are using **Rhino 6.0**, please execute the following command.&#x20;

```
python -m compas_rhino.install -v 6.0 --clean
```

If the plug-ins are installed correctly, you should see "Install completed" and no errors.
