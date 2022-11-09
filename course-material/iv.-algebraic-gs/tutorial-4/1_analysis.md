# 1. Analysis with IGS

**Learning goal:** How to analyse **two-dimensional frame structures** with graphic statics.

The tutorial will use the following template with the structures, please download and open it in Rhino 7.0:

{% file src="../../../../.gitbook/assets/CSDI_2021_tutorial.3dm" %}

## 1. Rules to define the diagrams

The following rules need to be observed to draw a form diagram representing the structure in IGS:

### **1.1. Forces and reactions drawn as edges**&#x20;

The representation of structures in IGS requires that the **loads applied** and **reaction forces** are drawn as edges in the diagram. The following examples represent possible inputs for IGS. In these, the black edges represent the internal members of the structure. The loads applied are represented in green and the supports, or reaction forces, are drawn in blue. The edges representing loads and supports will be indifferent in IGS, these will be called **leaf edges** in the diagram.

![](<../../../../.gitbook/assets/image (231).png>)

### **1.2. Sign to applied loads.**

After drawing the reaction forces as edges in the structure, we need to set the magnitude of the forces (i.e. 5 kN), as well as the sign of the structure to define whether the force is pressing against (-5 kN) the structure or pulling from the structure (+5 kN). The scheme below, show some possible load case applications in the triangulated truss. Note how confusion in the sign may completely change the way in which the forces are applied.

![](<../../../../.gitbook/assets/image (176).png>)

### **1.3. Identify and assign force to independent edges**

The forces can only be freely assigned to certain edges in a given form diagram. The number of edges that can be freely loaded corresponds to the same number of degrees of freedom of a given form diagram. The DOF can be calculated by the simple formula **** `DOF = m - 2*ni` **** where `m` is the number of edges in the diagram and `ni` is the number of internal vertices in the diagram. The internal vertices are highlighted in the examples below. For each of the examples below, the edges highlighted in purple represent a possible selection of the independent/loaded edges:

![](<../../../../.gitbook/assets/image (152).png>)

IGS checks the required number of independent edges via the button `Check DOF`.&#x20;

In this tutorial, we will deal with structures of **type A** and **type C.** Structures from **type B** will not be studied in this course.

### **1.4. Diagram must not contain edges overlapping and 2-valence nodes.**

Two constructive rules bust also be observed, as highlighted below. Nodes with only two edges (degree = 2) should not be drawn, which means there's no external force applied to the nodes. IGS will indeed delete such edges if they are drawn. Additionally, the diagram should contain no crossing edges.&#x20;

![](<../../../../.gitbook/assets/image (188).png>)

Now, let's dive into the examples.

## **2. Single panel truss**

The initial example is a single panel truss in which we will learn how to use the basic commands from IGS:

![](<../../../../.gitbook/assets/image (390).png>)

Click [here](1.1.-single-panel.md) for the full sigle panel truss tutorial.

## **3. Complete Truss Structure**

Now, let's follow together the examples of a more complex truss structure using IGS:

![](<../../../../.gitbook/assets/image (112) (1).png>)

Click [here](1.2.-complete-truss.md) for the full truss tutorial.

## **4. Force Control**

In the last example we will perform force-based modifications in the form diagram. We will modify the force diagram and search the geometry of the structure that meets such forces:

![](<../../../../.gitbook/assets/image (118).png>)

Click [here](1.3.-force-control.md) for the force control tutorial.

# 1. Single Panel

Let's start with the following simple example of a single panel truss. The geometry, loads and support conditions are depicted in the figure below:

![](<../../../../.gitbook/assets/image (110).png>)

The hypothesis of our analysis will be:

* The force applied on the top has magnitude of **10 kN**.
* The left support is a pin (restraint on x, y) and the right support a roller (restraint on y)

The set of lines for this exercise is available in the previous [page](./). As mentioned before, the load (blue) and reaction directions (green) are repressented as lines:

![](<../../../../.gitbook/assets/image (305).png>)

### 1. Making the Form Diagram

In the toolbar of IGS go to the function  `Create Form Diagram` and select the option `FromLines` . The FormDiagram will be created and you can notice a difference in the colour of **internal edges** (structure) and **external edges** (loads and reactions).

![](<../../../../.gitbook/assets/image (116).png>)

The Form Diagram edges will be stored in a new layer created, at `IGS >> FormDiagram`. The future Force Diagram will also be drawn in the dedicated created layer `IGS >> ForceDiagram`.

![](<../../../../.gitbook/assets/image (33).png>)

{% hint style="info" %}
The input lines will be hidden from the canvas, to avoid overlap with the newly created Form Diagram. If you need to view them again you need to type the command `Show` in Rhino, or click with the right button in the icon over the main toolbar, as shown below. The input edges should remain hidden during this tutorial.
{% endhint %}

![](<../../../../.gitbook/assets/image (227).png>)

### 2.2. Setting loaded edges&#x20;

The truss is an isostatic example in which there's only one load applied. We can chose the magnitude of this force freely. We could also apply the equation explained in the first part, here we have `m=7` edges and `ni=3` internal nodes (`DOF = m - 2*ni = 1`).&#x20;

Click over the Assign Forces button. Select the edge representing the load and apply a magnitude of **-10 kN** since the force should push the panel. The edges will display numered and in this case you should apply the force to the edge #0.

![](<../../../../.gitbook/assets/image (376).png>)

After we hit OK, the forces applied are shown in the edges with an arrow. Verify that the arrow direction corresponds to the desired direction of the applied loads.

![](<../../../../.gitbook/assets/image (371).png>)

### 2.3. Setting supports&#x20;

Supports should be assigned to the nodes where reaction forces are applied. Go to the function `Identify Anchors` and select the two nodes in the base of the single panel. These nodes will be highlighted in red as in the figure below:

![](<../../../../.gitbook/assets/image (323).png>)

### 2.4. Compute the Force Diagram&#x20;

After setting the loads we can compute the equilibrium by calculating the force diagram in the button `Create Force Diagram`, the force diagram is automatically generated right to the form diagram. The result should be as below:

![](../../../../.gitbook/assets/image.png)

Note that the reaction forces now display also the value and direction. The default visualisation for form and force is the red-blue colouring. **Blue** represents **compression** and **red** **tension**. At this point, the scale and location of the force diagram is automatically set by IGS.&#x20;

### 2.5. Display Settings

A series of display options can be modified to help to visualise the diagrams. These options are organised in the two tabs of the `Display Settings` menu: FormObject and Force Object, as depicted below:

![](<../../../../.gitbook/assets/image (274).png>)

Therefore, the red/blue colouring can be turned on and off (_forcecolors_). Equally the edge and vertex labels can be turned on and off. Additionally, force labels, indicating the magnitude the force on the edges are available for both diagrams. For the Form Diagram, pipes can be drawn in the edges with thickness proportional to the load carried. The scale of these pipes can also be modified in the display settings panel.&#x20;

The scale and the location of the Force diagram can be modified in the appropriate functions over the **IGS** Menu Display > `ForceDiagram Location` and `ForceDiagram Scale` .

### 2.6. Inspect Diagrams.

To analyse the magnitude of the forces in specific edges three options are available in the Button `Inspect Diagrams`. An **EdgesTable** can be displayed with information about all the forces in the structure, additionally, information about one specific edge of the structure can be queried with the option **EdgeInformation**, and the duality can be inspected with the function **ForcePolygons.**

![](<../../../../.gitbook/assets/image (150).png>)

![](<../../../../.gitbook/assets/image (97).png>)

![](<../../../../.gitbook/assets/image (2).png>)



# 1.2. Complete Truss

The second example analyses a truss structure to represent the following structure:

![](<../../../../.gitbook/assets/image (175).png>)

The hypothesis of our analysis will be:

* Forces applied at each node have a magnitude of **10 kN**.
* Reaction forces should be considered in the extreme left (vertical and horizontal) and extreme right (horizontal only).

### 1. Making Form Diagram.

As in the first example at IGS toolbar go to  `Create Form Diagram` and select the option `FromLines` . The created diagram should look like this:

![](<../../../../.gitbook/assets/image (386).png>)

### 2. Setting loaded edges.&#x20;

The truss is an isostatic example. It is composed of `m=33` edges and `ni=14` internal nodes. Therefore we are able to specify the force in 5 edges (`DOF = m - 2*ni = 5`) as explained in [Section 1,](./) which matches the number of externally applied loads. In IGS you can click the button `Check DoF` to check the required number of forces that should be selected.

We go to the command `Assign Forces` and we are asked to choose the independent edges, therefore we select the applied forces and input the corresponding force of +**10 kN** in each **** with the help of the table. This table shows the index of each edge in the column "Name" and the force should be assigned to the column "Value". The edge indices are shown in the diagram while the table is open to help the identification. Note the positive sign because the forces applied in the bottom chord tend to pull the structure down. Once we press `OK`, and the forces are assigned, and this can be checked by the colour-coding having the independent edges with **cyan** colour.

![](<../../../../.gitbook/assets/image (185).png>)

After we hit OK, the forces applied are shown in the edges with an arrow. Verify that the arrow direction corresponds to the desired direction of the applied loads. The supports don't show any value since the equilibrium has not been calculated yet.

![](<../../../../.gitbook/assets/image (373).png>)

### 3. Set the support points.&#x20;

Supports should be assigned to the nodes where reaction forces are applied. Go to the function `Identify Anchors` and select the two extreme nodes in the base of the truss. These nodes will be highlighted in red as in the figure below:&#x20;

![](<../../../../.gitbook/assets/image (86).png>)

### 4. Compute the Force Diagram.&#x20;

After setting the loads we can compute the equilibrium by calculating the force diagram in the button `Create Force Diagram`, the force diagram is automatically generated right to the form diagram. The result should be as below:

![](<../../../../.gitbook/assets/image (59).png>)

Note that the reaction forces now show the value and direction of its non-null resultants (25 kN up vertically). The default visualisation for form and force is the red-blue colouring. **Blue** represents **compression** and **red** for the edges in **tension**. At this point, the scale and location of the force diagram is automatically set by IGS. In the next section we will learn how to scale and position the diagram as required in this tutorial.

### 5. Scale and Location of the Force Diagram.&#x20;

The scale and location of the diagram can be set in the IGS Menu on Display > ForceDiagram location / ForceDiagram scale as shown in the image below. By using these you can position the force diagram in the box indicated.

![](<../../../../.gitbook/assets/image (337).png>)

Once the diagram is placed in the required location and scale, the maximum force in one edge can be easily calculated using the `inspector`, which is 45 kN and given the scale used 0.2 the edge in the force diagram has real length`L=45x0.2 = 9.0`

![](<../../../../.gitbook/assets/image (38).png>)

### 6. Exploring sturctural geometry

Geometric modifications, such as dragging nodes in the form diagram can be executed with the button `Move FormDiagram Nodes`. Once one modification is performed, the form diagram can be updated by pressing the button `Update ForceDiagram from FormDiagram`.&#x20;

One example of modification is done below: we move up one of the nodes of the structure, and as a result, a large force is attracted to the edge connected to it. This higher magnitude can be seen due to the increased size shown by it in the force diagram. The force magnitude rises from initially 7.1 kN to 37.9 kN.

![](<../../../../.gitbook/assets/image (112).png>)

![](<../../../../.gitbook/assets/image (271).png>)

![](<../../../../.gitbook/assets/image (405).png>)

(In the figure above, _forcepipes_ are activated so the new magnitude of the forces can be seen directly in the form diagram. To better visualise the pipes, the view is selected as ghosted with opacity 80%).

Additionally, feedback on the cost of the structure can be assessed by activating the option`Compute loadpath` that shows an increase in the cost/loadpath of the structure:

> The total load-path of the structure is 1962.3 kNm.

Further dragging of nodes can be executed, such as, increasing the structural height of the structure, what results in a global decrease on the forces in the members and also a reduction in the cost of the structure.

![](<../../../../.gitbook/assets/image (242).png>)

> The total load-path of the structure is 1326.6 kNm.



![](<../../../../.gitbook/assets/image (265).png>)

> The total load-path of the structure is 1425.3 kNm.

{% hint style="info" %}
An option to **auto-update** the diagrams is available in the display settings tabs and it is turned `OFF` by default. If `ON`, this function update the force diagram at each node movement of the form diagram.
{% endhint %}

### 7. Analysis of different Load Cases.

To finish we show how the load case could be changed. Since this corresponds to a triangulated (isostatic) structure different loads can be carried without changing its shape (unlike the [funicular arch](../2.-interactive-gs/)). Here the force applied in the highlighted position is increased from 10 kN to 30 kN to simulate the hanging of a very heavy object on the truss. We can see the increase in the loads in the internal edges. (In the following figure, _force pipes_ are also activated so the new magnitude of the forces can be seen directly in the form diagram).

![](<../../../../.gitbook/assets/image (352).png>)