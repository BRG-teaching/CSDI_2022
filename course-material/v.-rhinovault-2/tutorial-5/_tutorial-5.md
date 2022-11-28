# Tutorial

## Learning goals

* form-find funicular shell structures using Rhino Vault 2
* explore different shell structures using the features of Rhino Vault 2

## Content

This tutorial will teach you the basic capabilities of RV2. As not all capabilities of the software will be included, feel free to browse [the documentation](https://blockresearchgroup.gitbook.io/rv2/quick-start/tutorial) on your own at a later time and try out the other more advanced tutorials.

## 0. Initialisation

As with IGS, the first step is to initiate the RV2 engine which imports all the relevant packages and activates `compas_cloud` server. This requires clicking the ![](../../../.gitbook/assets/rv2\_toolbar\_init.png) icon or typing `_RV2_init`. The startup window also provides various links to useful information, such as the online documentation, tutorials, tutorials and terms of use. By clicking “YES,” you acknowledge that you have read and understood the Terms and Conditions, and the Data Donation Agreement.

<figure><img src="../../../.gitbook/assets/rv2_installRV2_init.png" alt=""><figcaption><p>Screen capture of the RV2 init window</p></figcaption></figure>

## 1.0 Simple Shell Formfinding from Lines

Let's start with the simplest workflow for using RV2, where we will make a simple shell supported at all its boundaries. In RV2, a **Pattern** is a collection of lines that define the topology of the form diagram. For this example we will use a simple grid of lines.

<figure><img src="../../../.gitbook/assets/rv2_tut_1_lines.png" alt=""><figcaption><p>Initial grid of lines</p></figcaption></figure>

### 1.1 Defining the Topology

Each line in the grid is a **segment**, meaning that these lines cannot run continuously from one side of the pattern to the other side and must instead be segmented into shorter lines per each quadrilateral in the pattern. The next step is to select In the toolbar of IGS2, click the button ![](../../../.gitbook/assets/rv2\_toolbar\_make\_pattern.png) `Create pattern` and select the option `FromLines`. Next, select the lines of the pattern. It should then look like this.

<figure><img src="../../../.gitbook/assets/rv2_tut_1_pattern.png" alt=""><figcaption><p>Pattern</p></figcaption></figure>

### 1.2 Identifying the Supports

The next step is to click the following series of commands: click the icon ![](../../../.gitbook/assets/rv2\_toolbar\_define\_boundaries.png) to `Define boundary conditions`. Then in the Rhino command line, click on `IdentifySupports`, `Select`, then `AllBoundaryVertices`. Next **press enter twice** to exit out of the command and end the process of defining the boundary conditions. You can confirm that the program executed the command correctly when you see that all vertices located at the boundary of the pattern are displayed in red.

<figure><img src="../../../.gitbook/assets/rv2_tut_1_supports.png" alt=""><figcaption><p>Support vertices</p></figcaption></figure>

### 1.3 Creating the Form Diagram

Now that we have given RV2 the general topology of the shell and identified the supports, it is time to make the form diagram. This is done by clicking the button ![](../../../.gitbook/assets/rv2\_toolbar\_form\_diagram.png) `Create form diagram`. You should now see a green mesh which represents the shell. Currently this mesh is flat as we have not finished the process. This is also indicated by the fact that the mesh is <mark style="color:green;">**green**</mark> which means that the mesh is **not in equilibrium**.

<figure><img src="../../../.gitbook/assets/rv2_tut_1_formDiagram.png" alt=""><figcaption><p>Form Diagram</p></figcaption></figure>

### 1.4 Creating the Force Diagram

The next step is to generate the force diagram. Unlike IGS, RV2 relies on an iterative solver and therefore the initial force diagram generated is actually the dual of the form diagram. We generate this diagram by clicking the button ![](../../../.gitbook/assets/rv2\_toolbar\_force\_diagram.png) `Create force diagram`. The diagram appears to the right of the form diagram.

<figure><img src="../../../.gitbook/assets/rv2_tut_1_forceDiagram.png" alt=""><figcaption><p>Initial Force Diagram</p></figcaption></figure>

While in IGS and our earlier work doing graphic statics by hand we have kept a parallel convention, RV2 does not use that convention. Instead, as presented in the lecture, RV2 uses a **perpendicular convention**. The red dots on the force diagrams with numbers therefore indicate the **angle deviation** of the force diagram, displaying the amount of degrees that those lines in the force diagram are off from being perpendicular to the corresponding edge in the form diagram.

In order to resolve this angle deviation, the next step is to find the horizontal equilibrium. This step initiates the iterative solver in RV2 which will change the force diagram from being the dual into the force diagram to find the **compression-only equilibrium** for the shell structure on the horizontal plane.

To do this, we click the button ![](../../../.gitbook/assets/rv2\_toolbar\_horiz\_equilibrium.png) `Horizontal equilibrium`. The command line then has three options : `Alpha`, `Iterations`, and `RefreshRate`. In this tutorial we will not change these options, however it is good to know that `Iterations` dictates how many times the solver for the horizontal equilibrium will run. This helps prevent crashing your computer should you try to find the equilbrium of a form and force diagram which cannot be in equilbrium, but also means that more complex diagrams require either running the `Horizontal equilibrium` command multiple times or increasing the number for `Iterations`.

The solver will run and adjust the force diagram, which in this example is quite simple. The numbers on the force diagram will disappear, and the command line will display the words "Horizontal equilibrium found!".

<figure><img src="../../../.gitbook/assets/rv2_tut_1_horizEquilibrium.png" alt=""><figcaption><p>Force Diagram in Horizontal Equilibrium</p></figcaption></figure>

### 1.4 Generating the Thrust Object

Next, we will click the button ![](../../../.gitbook/rv2\_toolbar\_vert\_equilibrium.png) `Vertical equilibrium` to find the vertical equilibrium of the shell structure and generate the thrust object (the mesh which represents the shell). RV2 will automatically calculate a height that is ideal for the shell structure based on self weight, however it is also possible to click on `TargetHeight` and change the value.

<figure><img src="../../../.gitbook/assets/rv2_tut_1_verticalEquilibrium.png" alt=""><figcaption><p>Vertical Equilibrium</p></figcaption></figure>

After running this step, you can see that the mesh has changed from <mark style="color:green;">**green**</mark> to <mark style="color:red;">**pink**</mark>. Whenever you are going through the workflow in RV2, keep this in mind at all times. If changes are made in the form or force diagrams, or to the thrust object itself, the equilibrium must be recalculated.

### 1.5 Saving the RV2 Results

Unlike IGS, there can only be one RV2 session running in Rhino at a time. Therefore, in order to keep your results and be able to continue your formfinding at a later time, you need to save out your RV2 files **.rv2** scene files. This can be easily done by clicking ![](../../../.gitbook/assets/rv2\_toolbar\_save\_scene.png) `Save RV2 session`. Similarly to grasshopper you can later open your base Rhino file, initialise RV2, and load these .rv2 scene files in order to recover your results by clicking ![](../../../.gitbook/assets/rv2\_toolbar\_load\_scene.png) `Open RV2 session`.

It is worth noting that you can save your rhino file from RV2 and still recover your final results, however without saving the RV2 session as a .rv2 file you will no longer be able to work on the shell and continue your formfinding.

### 1.6 Clearing the Scene

In order to move on to the next example, we have to clear out our RV2 session in order to start from scratch. You can easily do this by clicking ![](../../../.gitbook/assets/rv2\_toolbar\_clear\_scene.png) `Clear scene`.

## 2.0 Shell Formfinding from a Mesh and Different Visualisation Options

Now we will expand upon the simple workflow to make a simple shell supported at its four corner points. We will also go through different options for visualisation in RV2.
