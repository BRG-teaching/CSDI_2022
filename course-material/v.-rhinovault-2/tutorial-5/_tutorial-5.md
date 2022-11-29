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

The next step is to click the following series of commands: click the icon ![](../../../.gitbook/assets/rv2\_toolbar\_define\_boundaries.png) to `Define boundary conditions`. Then in the Rhino command line, click on `IdentifySupports`, `Select`, then `AllBoundaryVertices`. Next **press enter twice** to exit out of the command and end the process of defining the boundary conditions. You can confirm that the program executed the command correctly when you see that all vertices located at the boundary of the pattern are displayed in <mark style="color:red;">**red**</mark>.

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

Next, we will click the button ![](../../../.gitbook/assets/rv2_toolbar_vert_equilibrium.png) `Vertical equilibrium` to find the vertical equilibrium of the shell structure and generate the thrust object (the mesh which represents the shell). RV2 will automatically calculate a height that is ideal for the shell structure based on self weight, however it is also possible to click on `TargetHeight` and change the value.

<figure><img src="../../../.gitbook/assets/rv2_tut_1_verticalEquilibrium.png" alt=""><figcaption><p>Vertical Equilibrium</p></figcaption></figure>

After running this step, you can see that the mesh has changed from <mark style="color:green;">**green**</mark> to <mark style="color:magenta;">**pink**</mark>. Whenever you are going through the workflow in RV2, keep this in mind at all times. If changes are made in the form or force diagrams, or to the thrust object itself, the equilibrium must be recalculated.

### 1.5 Saving the RV2 Results

Unlike IGS, there can only be one RV2 session running in Rhino at a time. Therefore, in order to keep your results and be able to continue your formfinding at a later time, you need to save out your RV2 files **.rv2** scene files. This can be easily done by clicking ![](../../../.gitbook/assets/rv2\_toolbar\_save\_scene.png) `Save RV2 session`. Similarly to grasshopper you can later open your base Rhino file, initialise RV2, and load these .rv2 scene files in order to recover your results by clicking ![](../../../.gitbook/assets/rv2\_toolbar\_load\_scene.png) `Open RV2 session`.

It is worth noting that you can save your rhino file from RV2 and still recover your final results, however without saving the RV2 session as a .rv2 file you will no longer be able to work on the shell and continue your formfinding.

### 1.6 Clearing the Scene

In order to move on to the next example, we have to clear out our RV2 session in order to start from scratch. You can easily do this by clicking ![](../../../.gitbook/assets/rv2\_toolbar\_clear\_scene.png) `Clear scene`.

## 2.0 Formfinding from a Mesh and Visualisation Options

Before starting this example, it is important to know the difference between a mesh and a surface. 

- Rhino defines a [surface](http://docs.mcneel.com/rhino/5/help/en-us/seealso/sak_surface.htm#:~:text=A%20surface%20is%20like%20a,same%20object%3A%20a%20NURBS%20surface.) as being like a rectangular stretchy rubber sheet. The NURBS form can represent simple shapes, such as planes and cylinders, as well as free-form, sculptured surfaces.

- Rhino defines a [mesh](http://docs.mcneel.com/rhino/5/help/en-us/commands/mesh.htm#:~:text=The%20Mesh%20command%20creates%20a,export%20into%20various%20file%20formats.) as a collection of vertices and polygons that define the shape of an polyhedral object.

In summary, **meshes** are composed of faces, edges, and vertices while **surfaces** are best described as the pure mathematical expression of the geometry. 

Now that we know the difference, we can begin the example. Here we will expand upon the simple workflow to make a simple shell supported at its four corner points. We will also go through different options for visualisation in RV2.

### 2.1 Defining the Topology

We begin with a simple mesh with the same dimensions and subdivisions as our last example, as shown in Fig 2-1. 

<figure><img src="../../../.gitbook/assets/rv2_tut_2_initialGeom.png" alt=""><figcaption><p>Fig 2-1 : Initial Mesh</p></figcaption></figure>

First, we select ![](../../../.gitbook/assets/rv2_toolbar_make_pattern.png) `Create pattern` and select the option `FromMesh`. Next, select the mesh. It should then look like this.

<figure><img src="../../../.gitbook/assets/rv2_tut_2_meshPattern.png" alt=""><figcaption><p>Fig 2-2 : Pattern from Mesh</p></figcaption></figure>

### 2.2 Identifying the Supports

The next step is to click the following series of commands: click the icon ![](../../../.gitbook/assets/rv2\_toolbar\_define\_boundaries.png) to `Define boundary conditions`. Then in the Rhino command line, click on `IdentifySupports`, `Select`, then `Corners`. Press enter to allow RV2 to find and select the corners.

<figure><img src="../../../.gitbook/assets/rv2_tut_2_corners.png" alt=""><figcaption><p>Supports Located at the Corners</p></figcaption></figure>

At this point it is important to note that as a consequence of selecting only the four corners, we must now update our form diagram to accomodate for this choice. In order to understand how we must update our form diagram, we can isolate one vertex and graphically calculate the equilibrium of that node by drawing the force diagram (Fig 2-3 left). In the case on the left (straight boundaries), since the directions of the forces along the opening needs to be horizontal, you can not close the force polygon unless the force perpendicular to the opening is zero. However by updating the form diagram with a sag equal to 10% of the span of the opening, the force polygon can be closed using forces with finite magnitude (Fig 2-3 right).

<figure><img src="../../../.gitbook/assets/rv2_tut_2_corners.png" alt=""><figcaption><p>Fig 2-3 : Pattern with no sag (left) and pattern with 10% sag at the openings (right)</p></figcaption></figure>

This sag feature is available in RV2. In the Rhino command line, click on `UpdateBoundaries`. You will now see that each side of the pattern has received an identification number as in Fig 2-4.

<figure><img src="../../../.gitbook/assets/rv2_tut_2_sagStart.png" alt=""><figcaption><p>Fig 2-4 : Pattern with sides identified</p></figcaption></figure>

We can now change the amount of sag on individual boundaries, or one by one. We will go ahead and add a sag of 10% to all boundaries. Do this by clicking `All`, and then `Sag10`. We can see the sag that is applied to the sides in Fig 2-5. Now **press enter twice** to apply all the changes to the topology.

<figure><img src="../../../.gitbook/assets/rv2_tut_2_sag10.png" alt=""><figcaption><p>Fig 2-5 : 10% Sag applied to sides</p></figcaption></figure>

### 2.3 Creating the Form Diagram

Next we will create the form diagram as before by clicking  ![](../../../.gitbook/assets/rv2\_toolbar\_form\_diagram.png) `Create form diagram`. 

<figure><img src="../../../.gitbook/assets/rv2_tut_2_formDiagram.png" alt=""><figcaption><p>Fig 2-6 : Form Diagram</p></figcaption></figure>

### 2.4 Creating the Force Diagram

Now click ![](../../../.gitbook/assets/rv2\_toolbar\_force\_diagram.png) `Create force diagram`. In this example we can see many more dots indicating angle deviations, shown in Fig 2-7. This is resolved in the horizontal equilibrium step. To do this, we click the button ![](../../../.gitbook/assets/rv2\_toolbar\_horiz\_equilibrium.png) `Horizontal equilibrium`. If you run the solver once and there are remaining angle deviations, just run the `Horizontal equilbrium` command again. The final force diagram after solving for equilibrium is shown in Fig 2-8. 

<figure><img src="../../../.gitbook/assets/rv2_tut_2_forceDiagram.png" alt=""><figcaption><p>Fig 2-7 : Force Diagram not in Equilbrium</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/rv2_tut_2_horizEquilibrium.png" alt=""><figcaption><p>Fig 2-8 : Final Force Diagram in Equilibrium</p></figcaption></figure>

### 2.5 Generating the Thrust Object

Next, we will click ![](../../../.gitbook/assets/rv2_toolbar_vert_equilibrium.png) `Vertical equilibrium` to find the vertical equilibrium of the shell structure and generate the thrust object.

<figure><img src="../../../.gitbook/assets/rv2_tut_2_thrustObject.png" alt=""><figcaption><p>Fig 2-9 : Initial Thrust Object</p></figcaption></figure>

In this instance, let's change the height of the shell to see what happens. Click on ![](../../../.gitbook/assets/rv2_toolbar_vert_equilibrium.png) `Vertical equilibrium` again, and this time click on `TargetHeight` to edit the value. Type **2** and then hit enter **twice**. Now we can see a shallow shell with increasted reaction forces at the corners. 

<figure><img src="../../../.gitbook/assets/rv2_tut_2_thrustObject_2.png" alt=""><figcaption><p>Fig 2-10 : Thrust Object with 2m Height</p></figcaption></figure>

Next, let's increase the height to see the effect this has on the reaction forces. Click on ![](../../../.gitbook/assets/rv2_toolbar_vert_equilibrium.png) `Vertical equilibrium` again, and change the `TargetHeight` value to **6**. 

<figure><img src="../../../.gitbook/assets/rv2_tut_2_thrustObject_6.png" alt=""><figcaption><p>Fig 2-11 : Thrust Object with 6m Height</p></figcaption></figure>

We can see that this taller shell has decreased reaction forces at its corners in comparison to the shallow shell, as we would expect. While this visualisation is helpful, there are actually many other visualisation options in RV2 to help us more easily comprehend the force flow in the shell.

### 2.5 Visualisation Options

While we will not go over all the settings, we will go through a number of them which might be helpful for your. Click on ![](../../../.gitbook/assets/rv2_toolbar_settings.png) `Settings`. In the `RV2` tab, we can see the `angle tolerance` which determines the minimum value before RV2 displays the red dot with the angle deviation in the force diagram. The `forces` option color codes your form to your force diagram, allowing you to easily see which edges are taking the greatest forces. In Fig 2-12 the `forces` are shown.

<figure><img src="../../../.gitbook/assets/rv2_tut_2_settings_RV2.png" alt=""><figcaption><p>Fig 2-12 : RV2 Settings</p></figcaption></figure>

In the `FormObject` Tab we can show and hide the `edges` and the `vertices` of the form diagram. In Fig 2-13 the `edges` remain shown but the `vertices` have been hidden.

<figure><img src="../../../.gitbook/assets/rv2_tut_2_settings_ForceObject.png" alt=""><figcaption><p>Fig 2-13 : FormObject Settings</p></figcaption></figure>

In the `ForceObject` Tab we find the same types of settings, but now for the force diagram. In Fig 2-14 the `vertices` have been hidden and the `edges` are still shown.

<figure><img src="../../../.gitbook/assets/rv2_tut_2_settings_FormObject.png" alt=""><figcaption><p>Fig 2-14 : FormObject Settings</p></figcaption></figure>

The final tab `ThrustObject` has numerous helpful visualisation settings. Similar to our grasshopper exercises from before, we can do things such as show pipes. We are also able to display the stresses throughout the shell, color coding our form to our force diagram and increasing the speed with which we can analyse our results. Feel free to play around with these settings. In Fig 2-15, the `pipes` and `stresses` are shown.

<figure><img src="../../../.gitbook/assets/rv2_tut_2_settings_ThrustObject.png" alt=""><figcaption><p>Fig 2-15 : FormObject Settings</p></figcaption></figure>


## 3.0 Using Surfaces 
In order to use a surface, it must first be subdivided into a mesh object. In this example we will use **quadrilateral meshes** as they easier for RV2 to use, while there are also advantages and disadvantages to using this type of method versus **triangulation** (Example 4.0).

### 3.1 Subdivision Example 1

First we will input a surface with a number of curves to it.

<figure><img src="../../../.gitbook/assets/rv2_tut_3_input.png" alt=""><figcaption><p>Fig 3-1 : Input Surface</p></figcaption></figure>

Click ![](../../../.gitbook/assets/rv2\_toolbar\_make\_pattern.png) `Create pattern` and select the option `FromSurfaces`. RV2 will show you a grey linework representing a standard quadrilateral subdivision of the mesh (Fig 3-1), from which we will make adjustments.

<figure><img src="../../../.gitbook/assets/rv2_tut_3_subdivisionStep1.png" alt=""><figcaption><p>Fig 3-2 : Simple Subdivision</p></figcaption></figure>

We can now explore the different subdivision options. Click `SubdivideEntireMesh` and enter **8**. Now we can see the grey subdivision become much denser (Fig 3-3).

<figure><img src="../../../.gitbook/assets/rv2_tut_3_subdivision_8.png" alt=""><figcaption><p>Fig 3-3 : Densified Subdivision</p></figcaption></figure>

We can customise the subdivision further by selecting `SubdivideEdgeStrip` and clicking on the **black line** which represents the left edge of the surface. Type **4** and press enter. Now, we can see that RV2 has changed the subdivision in the direction of that edge to 4, and left the subdivision in the opposite direction unchanged. 

<figure><img src="../../../.gitbook/assets/rv2_tut_3_subdivision_8_4.png" alt=""><figcaption><p>Fig 3-4 : Edge Strip Subdivision</p></figcaption></figure>

### 3.1 Subdivision Example 2

Now let us look at a surface which causes some complications for RV2. This input surface is actually a series of surfaces joined together, some of which are triangles. Subdividing triangles into quadrilateral meshes requires the use of a specific subdivision method, which results in the triangles having a denser subdivision than adjacent quadrilaterals. 

Click ![](../../../.gitbook/assets/rv2\_toolbar\_make\_pattern.png) `Create pattern` and select the option `FromSurfaces`. Click on the second surface in the example file.

<figure><img src="../../../.gitbook/assets/rv2_tut_3_subdivisionStep1_2.png" alt=""><figcaption><p>Fig 3-5 : Simple Subdivision</p></figcaption></figure>

As you can see what were triangle surfaces are now subdivided into a denser mesh than other parts of the surface. Let's use the `SubdivideEdgeStrip` option and select one of the edges of the triangles. We see that RV2 alerts us that `This is a non-quadmesh strip - Choose an integer that is a power of 2`. Let's go ahead and type **2** and see what happens.

<figure><img src="../../../.gitbook/assets/rv2_tut_3_triangleEdge.png" alt=""><figcaption><p>Fig 3-5 : Simple Subdivision</p></figcaption></figure>

As you can see, some of the adjacent quadrilaterals were also effected by the change in the subdivision. We now have corners with a much higher subdivision than the rest of the shell. Let's see how this effects our formfinding. Hit enter to end the process, and let RV2 generate the pattern.

Click ![](../../../.gitbook/assets/rv2\_toolbar\_define\_boundaries.png) to `Define boundary conditions`. Then in the Rhino command line, click on `IdentifySupports`, `Select`, then `AllBoundaryVertices`. 

<figure><img src="../../../.gitbook/assets/rv2_tut_3_allBoundaries_ex2.png" alt=""><figcaption><p>Fig 3-5 : Simple Subdivision</p></figcaption></figure>

Next, generate the form and force diagram. Repeat the steps we've been doing, and if you have forgotten then scroll up on this tutorial page to find the icons and names of the commands again.

<figure><img src="../../../.gitbook/assets/rv2_tut_3_formandForce.png" alt=""><figcaption><p>Fig 3-5 : Simple Subdivision</p></figcaption></figure>

Now let's calculate the horizontal equilibrium.

<figure><img src="../../../.gitbook/assets/rv2_tut_3_horizEquilibrium.png" alt=""><figcaption><p>Fig 3-5 : Simple Subdivision</p></figcaption></figure>

Lastly, find the vertical equilibrium and generate the thrust object.

<figure><img src="../../../.gitbook/assets/rv2_tut_3_shell.png" alt=""><figcaption><p>Fig 3-5 : Simple Subdivision</p></figcaption></figure>

In this view we can see the effects of the much denser subdivision at the corners. The higher subdivision has resulted in a much flatter shell, even starting to bow outwards as it reaches the corners. While this is a compression only structure in equilibrium, its not an ideal solution. We can also see that the force distribution is not ideal in the force diagram, where the yellow edges are in a higher stress. 

### 3.1 Subdivision Example 3

Do this one Later.

## 4.0 Triangulation 
We have seen the quadrilateral mesh subdivision of surfaces, and will now explore a different method of subdivision : **triangulation**.

### 4.1 Defining the Topology

<figure><img src="../../../.gitbook/assets/rv2_tut_4_initialLines.png" alt=""><figcaption><p>Fig 4-1 : Input Lines</p></figcaption></figure>

We begin with a series of lines to guide our triangulation. First, we select ![](../../../.gitbook/assets/rv2_toolbar_make_pattern.png) `Create pattern` and select the option `FromTriangulation`. Next, select the outer outline as the **outer boundary** and press enter. Select the circle as the **inner boundary** and press enter.

An optional input of the triangulation process is to provide a constraint curve. This curve guides the triangulation subdivision such that the vertices and edges of the triangulation are aligned to this curve in order to include it in the topological generation.

The final step is to **Specify target edge length** which determines how large the triangles are. We will leave this value as **1** and press enter to finish the triangulation process.

<figure><img src="../../../.gitbook/assets/rv2_tut_4_triangulatedPattern.png" alt=""><figcaption><p>Fig 4-2 : Triangulation</p></figcaption></figure>

### 4.2 Identifying the Supports

Click ![](../../../.gitbook/assets/rv2\_toolbar\_define\_boundaries.png) to `Define boundary conditions`. Then in the Rhino command line, click on `IdentifySupports`, `Select`, then `AllBoundaryVertices`. 

We will now create our form and force diagrams, find the horizontal equilibrium, and analyse the results.

## 5.0 Creases : Two Methods 
We will now look at methods of interacting with the **force diagram** to affect our formfinding. 

### 5.1 Method One : Moving Vertices in the Force Diagram

The first method for adding creases to our shell is to move vertices in the force diagram and recalculate the equilibrium. 

#### 5.1.1 Topology Creation

We will start this process by clicking ![](../../../.gitbook/assets/rv2_toolbar_make_pattern.png) `Create pattern` and select the option `FromSurfaces`. Click on our surface. Click `SubdivideEdgeStrip`, select the left edge, and increase the subdivision to **8**. The result should look like Fig 5-1. 


<figure><img src="../../../.gitbook/assets/rv2_tut_5_creasePattern1.png" alt=""><figcaption><p>Fig 5-1 : Pattern for Crease</p></figcaption></figure>

#### 5.1.2 Define Supports

Next, define all the boundary vertices as supports. Do this by clicking ![](../../../.gitbook/assets/rv2\_toolbar\_define\_boundaries.png) to `Define boundary conditions`. Then in the Rhino command line, click on `IdentifySupports`, `Select`, then `AllBoundaryVertices`. It should look like Fig 5-2.

<figure><img src="../../../.gitbook/assets/rv2_tut_5_boundaryVertices_all.png" alt=""><figcaption><p>Fig 5-2 : Boundary Supports Defined</p></figcaption></figure>

#### 5.1.3 Find Initial Equilibrium

We will now find the initial shell without the crease applied. Generate the form and force diagrams, and then find the horizontal equilibrium. Then, find the vertical equilibrium. Your result should look like Fig 5-3.

<figure><img src="../../../.gitbook/assets/rv2_tut_5_creases_before.png" alt=""><figcaption><p>Fig 5-3 : Initial Shell Before Crease</p></figcaption></figure>

#### 5.1.4 Modify Force Diagram

We will now modify the force diagram to apply our creases. The first step is to click ![](../../../.gitbook/assets/rv2\_toolbar\_force\_settings.png) `Modify Force Diagram`. Then in the Rhino command line, click on `MoveVertices`. Select `Manual` and draw a box around a number of points from the force diagram and hit enter. Then, click on one of the points, and then click again to finalise the movement. See Fig 5-4 to see the steps.

<figure><img src="../../../.gitbook/assets/rv2_tut_5_steps_changeDiagram.png" alt=""><figcaption><p>Fig 5-4 : Initial Shell Before Crease</p></figcaption></figure>

The final force diagram should look something like this : 

<figure><img src="../../../.gitbook/assets/rv2_tut_5_forceDiagramModified.png" alt=""><figcaption><p>Fig 5-5 : Initial Shell Before Crease</p></figcaption></figure>

Now, we need to recalculate the horizontal equilibrium. Click the button ![](../../../.gitbook/assets/rv2\_toolbar\_horiz\_equilibrium.png) `Horizontal equilibrium`. Then click ![](../../../.gitbook/assets/rv2_toolbar_vert_equilibrium.png) `Vertical equilibrium` to also recalculate the vertical equilibrium. We now have our shell with two creases in it!

<figure><img src="../../../.gitbook/assets/rv2_tut_5_creaseShell1.png" alt=""><figcaption><p>Fig 5-6 : Initial Shell Before Crease</p></figcaption></figure>

### 5.2 Method Two : Setting Force Minimums and Maximums in the Force Diagram 

The second method for ...

## 6.0 Lip Edges

We will now take a look at how to manipulate the force diagram in order to achieve a lip at the edge of the shell. A nice example of this effect is Heinz Isler's Wyss Garten Haus, shown in Fig 6-1. 

<figure><img src="../../../.gitbook/assets/rv2_islerwyssgartenhaus_2.jpeg" alt=""><figcaption><p>Fig 6-1 : Close-up Photograph of Heinz Isler's Wyss Garten Haus [Link to Source](https://schoenstebauten.heimatschutz.ch/de/moderne-architektur-im-kanton-solothurn-1940-bis-1980)</p></figcaption></figure>

In order to make this change in the shell, we must **redirect** where our greatest forces will flow. Typically, in or shell formfinding (such as in Example 2.0) the greatest forces have been in the outermost edge of our shell, flowing down to the support points at the corners. In this case, we would like to have these greatest flowing through some edge that is not at the very outside of our shell. 

### 6.1 Defining the Topology

As in our other examples, the first step is to generate our topological pattern. Click the button ![](../../../.gitbook/assets/rv2\_toolbar\_make\_pattern.png) `Create pattern` and select the option `FromLines`. Select the lines of the pattern. 

<figure><img src="../../../.gitbook/assets/rv2_tut_6_pattern.png" alt=""><figcaption><p>Fig 6-1 : Pattern for Lip Example</p></figcaption></figure>

### 6.2 Identifying the Supports

The next step is to define the corners as our supports. Click ![](../../../.gitbook/assets/rv2\_toolbar\_define\_boundaries.png) to `Define boundary conditions`. Then in the Rhino command line, click on `IdentifySupports`, `Select`, then `Manual`. Now, select all the vertices at the top and bottom edges. it should look like Fig 6-2.

<figure><img src="../../../.gitbook/assets/rv2_tut_6_supportEdges.png" alt=""><figcaption><p>Fig 6-2 : Edges with Support Vertices Selected</p></figcaption></figure>

Next, click `UpdateBoundaries` and apply a sag of 10% to all boundaries. Do this by clicking `All`, and then `Sag10`. Your pattern should now look like Fig 6-3.

<figure><img src="../../../.gitbook/assets/rv2_tut_6_sagEdges.png" alt=""><figcaption><p>Fig 6-3 : Opposite Edges with Sag 10% Applied</p></figcaption></figure>

### 6.3 Form and Force Diagrams

Now that we have given RV2 the general topology of the shell and identified the supports, it is time to make the form diagram. Click ![](../../../.gitbook/assets/rv2\_toolbar\_form\_diagram.png) `Create form diagram`. Next, click ![](../../../.gitbook/assets/rv2\_toolbar\_force\_diagram.png) `Create force diagram` followed by ![](../../../.gitbook/assets/rv2\_toolbar\_horiz\_equilibrium.png) `Horizontal equilibrium`. You should now see the same thing as in Fig 6-3.

<figure><img src="../../../.gitbook/assets/rv2_tut_6_formandForce.png" alt=""><figcaption><p>Fig 6-3 : Form and Force Diagrams Generated, with Horizontal Equilibrium Found</p></figcaption></figure>

### 6.4 Formfound Geometry without Changes

Before we change the force digram, we will generate our shell **with a Target Height equal to 6** to see the existing concentrations of forces. 

<figure><img src="../../../.gitbook/assets/rv2_tut_6_initialShell.png" alt=""><figcaption><p>Fig 6-4 : Initial Shell</p></figcaption></figure>

Using our new insight on the RV2 settings, let's visualise the forces in the shell to more easily see the forces in the form diagram.

<figure><img src="../../../.gitbook/assets/rv2_tut_6_colorForceDiagram.png" alt=""><figcaption><p>Fig 6-5 : Color Coded Form and Force Diagrams</p></figcaption></figure>

Now we can clearly see that the longest edges in the force diagram, therefore the largest forces overall, are in the outer edges of the shell. One straightforward way to modify those large forces to be in an inner edge is to limit the amount of forces permitted in the outermost edges. 

The first step is to click ![](../../../.gitbook/assets/rv2\_toolbar\_force\_settings.png) `Modify Force Diagram`. Next, click `EdgesAttributes` and then `Manual`. Select the edges of the force diagram which are <mark style="color:red;">**red**</mark>, and press enter.

Click on the value for `lmax` and replace the old value with **1.5**. Press enter, then click `OK`. Your screen should look like this:

<figure><img src="../../../.gitbook/assets/rv2_tut_6_colorForceDiagram_postMod.png" alt=""><figcaption><p>Fig 6-6 : Thrust Object after Modifying Force Diagram</p></figcaption></figure>

You might have noticed that nothing really changed, except the color of the thrust object. It is important to note that the thrust object has now turned <mark style="color:green;">**green**</mark>, indicating that it is out of date and must be updated. 

The first step is to again find the horizontal equilibrium, so click ![](../../../.gitbook/assets/rv2\_toolbar\_horiz\_equilibrium.png) `Horizontal equilibrium`. It should look like Fig 6-7:

<figure><img src="../../../.gitbook/assets/rv2_tut_6_updatedForceDiag_postMod.png" alt=""><figcaption><p>Fig 6-7 : Updated Force Diagram</p></figcaption></figure>

We see now that the edges of the force diagram we constrained to have an `lmax` of **1.5** have shrunken significantly and are now green, indicating they are taking less forces. We see now that as a result, the lines for the edge which lies behind the outer edge are now red and taking most of the forces. Let's generate our thrust object to see the effect in 3D by clicking ![](../../../.gitbook/assets/rv2_toolbar_vert_equilibrium.png) `Vertical equilibrium`.

<figure><img src="../../../.gitbook/assets/rv2_shell_postMod_1.png" alt=""><figcaption><p>Fig 6-8 : Updated Thrust Object Perspective</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/rv2_shell_postMod_2.png" alt=""><figcaption><p>Fig 6-8 : Updated Thrust Object Front View</p></figcaption></figure>


We can see the lip which is now a part of the shell form happening over the openings. With more modification, we could turn this into a more dramatic effect by moving the lip more inwards or modifying the force diagram in other ways. 




## 7.0 Holes

## 8.0 Dropdowns