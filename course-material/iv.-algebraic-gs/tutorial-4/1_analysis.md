# Tutorial

## Learning Goals



* &#x20;analyze 2-dimensional truss structures with algebraic graphic statics
* form-find funicular and arch-cable structures with restrained algebraic graphic statics



## Content

We have learned how to find a form under variable loads using procedure graphic statics. However, when we want to modify the initial setup of the drawing, such as the number of structural elements and the connectivity, we need to modify a large amount of the program or even reconstruct the entire procedure. This process can be time-consuming and requires profound familiarity with geometric construction knowledge.  This week we will algebraic graphic statics to analyze 2-dimensional trusses, as well as form-find funicular and arch structures.&#x20;

## Arch-cable and Truss



###

---

## 1. Analysis of a Simple Truss

Let's start with the following example of the simple truss. The geometry, loads, and support conditions are depicted in the Fig-XXX. The left load is 30 kN and the right one 10 kN. 

<p align="center">
    <img src="../../../.gitbook/assets/simple_truss_diagram.png" alt="drawing" width="600"/>
</p>

#### 1.1 Making the Form Diagram
In the Rhino file, lines of of this truss are already drawn as Fig-XXX(top-left). The fixed support is represented by two reaction forces in x and y directions. The roller support is represented by a reaction force in y direction. Two unsymmetrical external forces are simplified as two lines in the orientation of the forces. 

In the toolbar of IGS go to the function `Create Form Diagram` and select the option `FromLines`.  The FormDiagram will be created as Fig-XXX(top-right). You can notice a difference in the colour of **internal edges** (structure) and **external edges** (loads and reactions). The Form Diagram edges are stored in a new Rhino layer - `IGS >> FormDiagram`.

![](<../../../.gitbook/assets/simple_truss_form.jpg>)


{% hint style="info" %}
The input lines will be hidden from the canvas, to avoid overlap with the newly created Form Diagram. If you need to view them again you need to type the command `Show` in Rhino, or click with the right button in the icon over the main toolbar, as shown below. The input edges should remain hidden during this tutorial.
{% endhint %}


The system has `m=10` edges and `ni=4` internal nodes. According to the definition of static determinacy, `DOF = m - 2*ni = 10 - 2*4 = 2`. We need to assign two forces. In IGS you can also click the button `Check DoF` to check the required number of forces that should be selected.
Click over the Assign Forces button. Select the two edges representing the loads and apply a magnitude of **-30 kN** to the left load and **-10 kN** to the right node. You can identify the left and right edges by the displayed numbers in edge labels. After we hit OK, the forces applied are shown in the edges with an arrow(Fig-XXX(bottom-left)). Verify that the arrow direction corresponds to the desired direction of the applied loads.


Supports should be assigned to the nodes where reaction forces are applied. Go to the function `Identify Anchors` and select the two nodes in the base of the single panel. These nodes will be highlighted in red(Fig-XXX(bottom-right)).

#### 1.2. Computing the Force Diagram

After setting the loads we can compute the equilibrium by calculating the force diagram in the button `Create Force Diagram`, the force diagram is automatically generated right to the form diagram. The result should be as FigXXX:

![](../../../.gitbook/assets/simple_truss_force.png)

Note that the reaction forces now display also the value and direction. The default visualisation for form and force is the red-blue colouring. **Blue** represents **compression** and **red** **tension**. At this point, the scale and location of the force diagram is automatically set by IGS.

In procedure graphic statics, the magnitude of the force is equal to the length of the force diagram. In IGS, the force diagram is automatically scaled in case the user accidently assign a gigantic force magnitude. To analyse the magnitude of the forces in specific edges three options are available in the Button `Inspect Diagrams`. An **EdgesTable** can be displayed with information about all the forces in the structure, additionally, information about one specific edge of the structure can be queried with the option **EdgeInformation**, and the duality can be inspected with the function **ForcePolygons.**

![](../../../.gitbook/assets/simple_truss_force_inspector.png)

For the Form Diagram, pipes can be drawn in the edges with thickness proportional to the load carried.

![](../../../.gitbook/assets/simple_truss_force_pipes.png)

---

## 2. Analysis of a Warren Truss with Vertical Supports
The second example analyses a warren truss with vertical supports(Fig-XXX). The forces applied at each node have a magnitude of 10 kN.

<p align="center">
    <img src="../../../.gitbook/assets/truss.png" alt="drawing" width="800"/>
</p>


#### 2.1 Making the Form Diagram

As in the first example, at IGS toolbar go to `Create Form Diagram` and select the option `FromLines` . This formdiagram is composed of `m=33` edges and `ni=14` internal nodes. Therefore we are able to specify the force in 5 edges (`DOF = m - 2*ni = 33 - 2*14 = 5`). Therefore, we use `Assign Forces` to select 5 forces and input the corresponding force of +**10 kN**. Use `Identify Anchors` to select the support nodes. (Fig_XXX)

![](../../../.gitbook/assets/truss_fixed.png)

#### 2.2. Computing the Force Diagram

After setting the loads we can compute the equilibrium by calculating the force diagram in the button `Create Force Diagram`, the force diagram is automatically generated right to the form diagram. The result should be as below(Fig_XXX). 

![](../../../.gitbook/assets/truss_force.png)


The scale and location of the diagram can be set in the IGS Menu on `Display` > `ForceDiagram location` / `ForceDiagram scale` as shown in the image below. By using these you can position the force diagram in the box indicated.

![](../../../.gitbook/assets/truss_scale.png)

Once the diagram is placed in the required location and scale, the maximum force in one edge can be easily calculated using the `inspector`, which is 45 kN and given the scale used 0.2 the edge in the force diagram has real length`L=45x0.2 = 9.0`

![](<../../../.gitbook/assets/image (38).png>)

#### 6. Exploring sturctural geometry

Geometric modifications, such as dragging nodes in the form diagram can be executed with the button `Move FormDiagram Nodes`. Once one modification is performed, the form diagram can be updated by pressing the button `Update ForceDiagram from FormDiagram`.

One example of modification is done below: we move up one of the nodes of the structure, and as a result, a large force is attracted to the edge connected to it. This higher magnitude can be seen due to the increased size shown by it in the force diagram. The force magnitude rises from initially 7.1 kN to 37.9 kN.

![](<../../../.gitbook/assets/image (112).png>)

![](<../../../.gitbook/assets/image (271).png>)

![](<../../../.gitbook/assets/image (405).png>)

(In the figure above, _forcepipes_ are activated so the new magnitude of the forces can be seen directly in the form diagram. To better visualise the pipes, the view is selected as ghosted with opacity 80%).

Additionally, feedback on the cost of the structure can be assessed by activating the option`Compute loadpath` that shows an increase in the cost/loadpath of the structure:

> The total load-path of the structure is 1962.3 kNm.

Further dragging of nodes can be executed, such as, increasing the structural height of the structure, what results in a global decrease on the forces in the members and also a reduction in the cost of the structure.

![](<../../../.gitbook/assets/image (242).png>)

> The total load-path of the structure is 1326.6 kNm.

![](<../../../.gitbook/assets/image (265).png>)

> The total load-path of the structure is 1425.3 kNm.

{% hint style="info" %}
An option to **auto-update** the diagrams is available in the display settings tabs and it is turned `OFF` by default. If `ON`, this function update the force diagram at each node movement of the form diagram.
{% endhint %}

#### 7. Analysis of different Load Cases.

To finish we show how the load case could be changed. Since this corresponds to a triangulated (isostatic) structure different loads can be carried without changing its shape (unlike the [funicular arch](../2.-interactive-gs)). Here the force applied in the highlighted position is increased from 10 kN to 30 kN to simulate the hanging of a very heavy object on the truss. We can see the increase in the loads in the internal edges. (In the following figure, _force pipes_ are also activated so the new magnitude of the forces can be seen directly in the form diagram).

![](<../../../.gitbook/assets/image (352).png>)


#### 2.5. Display Settings

A series of display options can be modified to help to visualise the diagrams. These options are organised in the two tabs of the `Display Settings` menu: FormObject and Force Object, as depicted below:

![](<../../../.gitbook/assets/image (274).png>)

Therefore, the red/blue colouring can be turned on and off (_forcecolors_). Equally the edge and vertex labels can be turned on and off. Additionally, force labels, indicating the magnitude the force on the edges are available for both diagrams. For the Form Diagram, pipes can be drawn in the edges with thickness proportional to the load carried. The scale of these pipes can also be modified in the display settings panel.

The scale and the location of the Force diagram can be modified in the appropriate functions over the **IGS** Menu Display > `ForceDiagram Location` and `ForceDiagram Scale` .

#### 2.6. Inspect Diagrams.

To analyse the magnitude of the forces in specific edges three options are available in the Button `Inspect Diagrams`. An **EdgesTable** can be displayed with information about all the forces in the structure, additionally, information about one specific edge of the structure can be queried with the option **EdgeInformation**, and the duality can be inspected with the function **ForcePolygons.**

![](<../../../.gitbook/assets/image (150).png>)

![](<../../../.gitbook/assets/image (97).png>)

![](<../../../.gitbook/assets/image (2).png>)