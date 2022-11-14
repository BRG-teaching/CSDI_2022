# Tutorial

## Tutorial

### Learning Goals

* analyze 2-dimensional truss structures using algebraic graphic statics
* form-find funicular arch-cable structures using restrained algebraic graphic statics

### Content

We have learned how to find a form under variable loads using procedure graphic statics. However, when we want to modify the initial setup of the drawing, such as the number of structural elements and the connectivity, we need to modify a large amount of the program or even reconstruct the entire procedure. This process can be time-consuming and requires profound familiarity with geometric construction knowledge. This week we will algebraic graphic statics to analyze 2-dimensional trusses, as well as form-find funicular and arch structures.

### Arch-cable and Truss

####

***

### 1. Analysis of a Simple Truss

Let's start with the following example of the simple truss. The geometry, loads, and support conditions are depicted in the Fig-XXX. The left load is 30 kN and the right one 10 kN.

![drawing](../../.gitbook/assets/simple\_truss\_diagram.png)

**1.1 Making the Form Diagram**

In the Rhino file, lines of of this truss are already drawn as Fig-XXX(top-left). The fixed support is represented by two reaction forces in x and y directions. The roller support is represented by a reaction force in y direction. Two unsymmetrical external forces are simplified as two lines in the orientation of the forces.

In the toolbar of IGS go to the function `Create Form Diagram` and select the option `FromLines`. The FormDiagram will be created as Fig-XXX(top-right). You can notice a difference in the colour of **internal edges** (structure) and **external edges** (loads and reactions). The Form Diagram edges are stored in a new Rhino layer - `IGS >> FormDiagram`.

![](../../.gitbook/assets/simple\_truss\_form.jpg)

{% hint style="info" %}
The input lines will be hidden from the canvas, to avoid overlap with the newly created Form Diagram. If you need to view them again you need to type the command `Show` in Rhino, or click with the right button in the icon over the main toolbar, as shown below. The input edges should remain hidden during this tutorial.
{% endhint %}

The system has `m=10` edges and `ni=4` internal nodes. According to the definition of static determinacy, `DOF = m - 2*ni = 10 - 2*4 = 2`. We need to assign two forces. In IGS you can also click the button `Check DoF` to check the required number of forces that should be selected. Click over the Assign Forces button. Select the two edges representing the loads and apply a magnitude of **-30 kN** to the left load and **-10 kN** to the right node. You can identify the left and right edges by the displayed numbers in edge labels. After we hit OK, the forces applied are shown in the edges with an arrow(Fig-XXX(bottom-left)). Verify that the arrow direction corresponds to the desired direction of the applied loads.

Supports should be assigned to the nodes where reaction forces are applied. Go to the function `Identify Anchors` and select the two nodes in the base of the single panel. These nodes will be highlighted in red(Fig-XXX(bottom-right)).

**1.2. Computing the Force Diagram**

After setting the loads we can compute the equilibrium by calculating the force diagram in the button `Create Force Diagram`, the force diagram is automatically generated right to the form diagram. The result should be as FigXXX:

![](../../.gitbook/assets/simple\_truss\_force.png)

Note that the reaction forces now display also the value and direction. The default visualisation for form and force is the red-blue colouring. **Blue** represents **compression** and **red** **tension**. At this point, the scale and location of the force diagram is automatically set by IGS.

In procedure graphic statics, the magnitude of the force is equal to the length of the force diagram. In IGS, the force diagram is automatically scaled based on the size of the form diagram, in case the user accidently assign a gigantic axial force. To analyse the magnitude of the forces in specific edges three options are available in the Button `Inspect Diagrams`. An **EdgesTable** can be displayed with information about all the forces in the structure, additionally, information about one specific edge of the structure can be queried with the option **EdgeInformation**, and the duality can be inspected with the function **ForcePolygons.**

![](../../.gitbook/assets/simple\_truss\_force\_inspector.png)

For the Form Diagram, pipes can be drawn in the edges with thickness proportional to the load carried.

![](../../.gitbook/assets/simple\_truss\_force\_pipes.png)

***

### 2. Analysis of a Warren Truss with Vertical Supports

The second example analyses a warren truss with vertical supports(Fig-XXX). The forces applied at each node have a magnitude of 10 kN.

![drawing](../../.gitbook/assets/truss.png)

**2.1 Making the Form Diagram**

As in the first example, at IGS toolbar go to `Create Form Diagram` and select the option `FromLines` . This formdiagram is composed of `m=33` edges and `ni=14` internal nodes. Therefore we are able to specify the force in 5 edges (`DOF = m - 2*ni = 33 - 2*14 = 5`). Therefore, we use `Assign Forces` to select 5 forces and input the corresponding force of +**10 kN**. Use `Identify Anchors` to select the support nodes. (Fig\_XXX)

![](../../.gitbook/assets/truss\_fixed.png)

**2.2. Computing the Force Diagram**

After setting the loads we can compute the equilibrium by calculating the force diagram in the button `Create Force Diagram`, the force diagram is automatically generated right to the form diagram. The result should be as below(Fig\_XXX).

![](../../.gitbook/assets/truss\_force.png)

The sum of external forces are `10 * 5 = 50 kN`. Turn on the hidden Rhino layer `Tutorial >> Guides`, you will find a 5m\*5m box. Now scale the force diagram so that 1m represents 10kN. The scale and location of the diagram can be set in the **IGS Menu** (not IGS Toolbar) on `Display` > `ForceDiagram location` / `ForceDiagram scale` as shown in the Fig\_XXX.

![](../../.gitbook/assets/truss\_scale\_pipe.png)

**2.3 Modification of Form Diagram**

Geometric modifications, such as dragging nodes in the form diagram can be executed with the button `Move FormDiagram Nodes`. Once one modification is performed, the form diagram can be updated by pressing the button `Update ForceDiagram from FormDiagram`.

One example of modification is done below: we move up one of the nodes of the structure, and as a result, a large force is attracted to the edge connected to it. This higher magnitude can be seen due to the increased size shown by it in the force diagram(Fig\_XXX).

![](../../.gitbook/assets/truss\_form\_mod.png)

If we increase the height of our truss, the internal forces decrease(Fig\_XXX).&#x20;

<figure><img src="../../.gitbook/assets/truss_form_mod2.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
An option to **auto-update** the diagrams is available in the display settings tabs and it is turned `OFF` by default. If `ON`, this function update the force diagram at each node movement of the form diagram.
{% endhint %}

**Special Case**

The following geometry shows a truss that is designed by the desired force property. It has constant axial forces in the bottom chord. The forces in the diagonal struts are zero. In the force diagram, the end points representing these diagonal struts are overlaid, which means the edges are of 0 length. Thus, these members can be eliminated from the structure if the chords have sufficient strength and flexural stiffness to satisfy the demand of non-uniform load cases and stability requirements.

![](../../.gitbook/assets/truss\_cons.png)

Now change the uniform loading to ununiform loading.

![](../../.gitbook/assets/truss\_cons\_unsymmetrical.png)

**2.4 Load Path (maybe delete??)**

Additionally, feedback on the cost of the structure can be assessed by activating the option`Compute loadpath` that shows an increase in the cost/loadpath of the structure. For Fig\_XXX,

> The total load-path of the structure is 1860.0 kNm.

For Fig\_XXX(high one),

> The total load-path of the structure is 1892.0 kNm.

---

## 3. Form finding of arch under uniformly distributed load

In procedure graphic statics, we use both the form diagram and force diagram to find a funicular structure in equilibrium. Here we will use algebric graphic statics to find an arch under uniformly distributed load. The load in each node is equal to **10 kN**.

![](../../.gitbook/assets/arch\_q.png)

In algebric graphic statics, we always need to start from a desired topology.&#x20;

In algebric graphic statics, we always need to start from a desired topology. The following steps are shown in Fig-XX. We assume that the two extremities are pin supports. We divide the line between two supports into 7 segments, and the points indicates the line of action of the vertical loads. Here we will use an arc of a circle as an initial guess. Intersect the vertial lines with the arc and redraw the arc as line segments. Hide auxiliary geometries and add lines that represent external forces on the nodes. This is our input geometry for the force diagram. 

![](<../../.gitbook/assets/arch_circle.jpg>)

### 1.1 Analysis of the circular arch
In this case, we have a funicular circular arch system, but the load is unknown. As long as we know one axial force in our system, we can draw the force diagram with the correct scale. We can double check this argument via the definition of static determinacy. The system has `m=17` edges and `ni=8` internal nodes. Its `DOF = m - 2*ni = 17 - 2*8 = 1`. We need to assign only one forces. 

Create FormDiagram with the function `Crerate Form Diagram` from the lines. Assign one load, -10 kN, with the button `Assign Forces`. Restrain the two extremity vertices assigning it as supports/anchors with the button `Identify Anchors`. Press the button `Create Force Diagram` which generated the ForceDiagram highlighted in Fig-XX.

![](<../../.gitbook/assets/arch_force.png>)

We observe that the force 10 kN is only applied to the edge selected as independent and the edge mirrored in the form diagram. The rest of applied loads are different to 10 kN. 

### 1.2 Constrained Equilibrium under Uniformilly Distributed Load 

In algebric graphic statics, modifing a force diagram to update the form diagram sometimes is not as straight-forward. These constraints will help the user to update the diagrams more easily, and 
our algorithm to converge more sufficiently. 

Four types of constraints are possible in the current version of IGS (Fig_XX)
  1. **Anchor a vertex**, fixing its x, y coordinates;
  2. Constraint a vertex to a **line of action**;
  3. Constraint **edge direction**; and&#x20;
  4. Apply **target forces** in the form diagram which reflect in target lengths in the force diagram.

![](<../../.gitbook/assets/image(408).png>)

{% hint style="info" %}
Since white is the default color for the constraints remember to change your backgroud color. Grey is prefered. The visualisation of the arch after the default constrains should look as follows:
{% endhint %}

To achieve the geometry corresponding to the uniformilly distributed load from our hypothesis, we will firstly add default constraints. Default constraint is implicit when we do graphic statics by hand. On the form diagram (Fig_XXX): 
   - the vertices in the form diagram with an externally applied load are constrained to remain on the line of action of the load (constraint type 2);
   - the leaf-edges (reactions or loads) have their orientation fixed (constraint type 3).
  
![](<../../.gitbook/assets/arch_constraint.png>)

Assign the default constraint by clicking `Assign default constraints` (Fig_XXX). We wee that: 
* Edges in the form and force diagrams with orientation fixed are highlighted in white.
* Vertices in the form and force diagram with line constraint are highlighted in white.
* Anchored vertices are shown in red.

![](<../../.gitbook/assets/default_constraint.png>)

Secondly, we assign **target forces** to the load edges with the same magnitude of the applied load. This reflect as a constraint on the **target length** of the dual edges in the force diagram. To assign these additional constraints click on the button `Assign edge constraints` and select the option `ForceMagnitude`. Select all applied loads and give the target magnitude (10 kN). The sign +/- is not important here since it will always take the same sign of the applied load. The target forces will show in white in the form and force diagrams (Fig_XXX).

![](<../../.gitbook/assets/arch_edge_force.png>)

Now, we applied constraints to the form and force diagrams which force them to look for a new equilibrium. Now we can update both the form and force diagrams (bi-directional update). Turn on  bi-directional update in the <img src="../../../../.gitbook/assets/image (36).png" alt="" data-size="line">`Settings`. If you continue without turning it on you will receive an error message.

Now that the bi-directional module is activated you click on  <img src="../../../../.gitbook/assets/image (75).png" alt="" data-size="line">`Update Both Diagrams`. Both diagrams will update and the result should be as displayed below (Fig_XXX):

![](<../../.gitbook/assets/arch_update_both.png>)

The funicular form for a uniformly distributed load is shalower than the original. The geometry is a parabola instead of an arc of a circle. 


![](<../../.gitbook/assets/igs_force_without_constraint.png>)


{% hint style="info" %}

The constraints can be turned on and off, in the latter the original force in the edge is displayed. Aditionally in the `Inspect diagrams > ConstraintsTable` a table is called showing all constraints and the current force in the edges, as well as the constraints in the vertices applied.

The constraints can be erased from the form on the Menu function `IGS> Constraints> Remove all constraints.`
{% endhint %}



---




### 4. Additional modifications

If the constraints are not erased, or are reassigned more modificaitions could be done on top of the current design. We will explore two simple ones. In the first modification we move one of the supports as in the image below:

![](<../../.gitbook/assets/image (314).png>)

We then press in the button Update both diagrams and both diagrams are matched according to the constraints and the new support position. The resultant structure is still a funicular for the uniformelly distributed load case but with supports in different elevations which make the vertical reaction forces unbalanced: 38.3kN and 21.7 kN as shown in the next figure:

![](<../../.gitbook/assets/image (109).png>)

The second additional modification imposes an additional target force to one of the reaction forces. Here we set the horizontal reaction force to have magnitude of 30 kN. As a result, the funicular change its height and in the force polygon the horizontal reaction force has its length decreased. The following images show this modifications.

![](<../../.gitbook/assets/image (120).png>)

![](<../../.gitbook/assets/image (363).png>)

Many more modifications are possible and playing around with the previous unidirectional is still possible.

## 2.2. Constant Force

The last example deals with the following non-triangulated truss:

![](<../../.gitbook/assets/image (50).png>)

This truss was form found to a equally distributed load which we will assume here as **10 kN** at each node. We want to compute the equilibrium and generate the force diagram for this structure and perform bi-directional modifications with IGS.

#### 1. Form Diagram with loads and support

We input the FormDiagram with the function `Create FormDiagram` using the lines provided in the Rhino file, applied loads and reactions are translated as lines in the diagram. The result look like this:

![](<../../.gitbook/assets/image (378).png>)

Now we assign loads with the button `Assign Forces`. This predefined shape allows the selection of only one independent edge. We select one of the edges representing the applied loads and assign the load **+10**. Here edge #13 was selected.

![](<../../.gitbook/assets/image (277).png>)

We press OK and validate the sign of the applied load, we must also restraint the two extremities vertices assigning it as supports/anchors using the button `Identify Anchors`. The result will look like the following image:

![](<../../.gitbook/assets/image (98).png>)

With this information updated we can go to the drawing of the Force Diagram.

#### 2. Drawing of the Force Diagram

We press the button `Create Force Diagram` which generated the ForceDiagram highlighted in the following image. We observe that the force 10 kN is not only applied to the edge selected as independent but also to the other applied loads. Therefore the input geometry was already form-found to such load case. The reaction forces are ballanced on the vertical 20 kN at each support.

![](<../../.gitbook/assets/image (45).png>)

Anoter particularity of this solution is that the bottom chord has constant tensile force equals 31.2 kN (edges 0, 1, 5, 16, 18) while in the upper chord the forces vary from 37.1 kN (edges 20, 10) to 31.2 kN (edge 9). The following can be observed with the tools available over the `Inspect Diagrams` function, such as the `EdgesTable` shown below:

![](<../../.gitbook/assets/image (380).png>)

On the next section we will impose constraints to form find the truss such as the edges in the top chord have constant force equals 30 kN.

#### 3. Impose constraints to the problem.

We will apply the required constraints in 4 steps:

First, the default constraints are applied affecting the leaf edges (loads and reactions) and the vertices connected to it. This can be done pressing the button `Apply Default Constraints`.

![](<../../.gitbook/assets/image (268).png>)

Second, we assign target forces to the top chord. In the button `Assign edge constraints` over the option `ForceMagnitude` we assign 30 kN to edges 7, 9, 10, 11, 20.

![](<../../.gitbook/assets/image (297).png>)

Third, multiple solutions for a constant top chord exist, in this tutorial we will intially look for the one which keep the bottom chord flat. To do that we click once more to the `Assign edge constraint` button over the option `EdgeOrientation` and select edges 0, 1, 5, 16, 18 in the bottom chord. The display should look like below:

![](<../../.gitbook/assets/image (124).png>)

Finally, to preserve the load case we assign target edges also to the applied loads. On the function `Assign edge constraints` option `ForceMagnitude` we assign 10 kN to the applied loads. The result look like below:

![](<../../.gitbook/assets/image (289).png>)

Once the constraints above are set we can go to the bi-directional update of the form and force diagrams.

#### 4. Bi-directional update

To update the diagrams, we click on the button `Update both diagrams`. The result is depicted below:

![](<../../.gitbook/assets/image (389).png>)

On the image below we see the overlap of the initial and final solutions. The dual edges of the top chord need to be moved to a circle with radius equals 30 kN. The modifications that would have to be done manually are displayed in the next Figure:

![](<../../.gitbook/assets/image (76).png>)

#### 5. Additional modifications

One additional modification will be performed. The top and bottom chord are constrained to the same target force 30 kN. As a consequence the bottom chord can no longer be flat. Therefore we remove that constraint and assign target edges to the bottom chord. The final state of the constraints applied should look like below:

![](<../../.gitbook/assets/image (252).png>)

Now, we can apply the update to form and force diagrams and the result is the double constant truss below:

![](<../../.gitbook/assets/image (156).png>)

#### 5. Advanced visualisation

To finalise we show a few advanced visualisations available in IGS. On the settings menu the diagram can be rotated of 90 degrees. In this way when the diagrams are in equilibrium the form and force corresponding edges are perpendicular to each other instead of parallel. The figure below shows how to activate this function on the ForceObject Settings.

![](<../../.gitbook/assets/image (43).png>)

An extra visualisation is available with the Unified Diagram. This diagram unifies form and force diagram in the same plot. Different unified diagrams can be drawn for different values of alpha. Alpha is de parameter that changes the shape of the unified diagram to follow form or force. On the figure below you see the final example of this page with the unified diagram for different alphas. More about this topic will be studied in our last module [3D graphic statics](broken-reference/).

![](<../../.gitbook/assets/image (29).png>)

That's it! You made the tutorial 4. If you want to learn even more dive in the [extra examples](../3.-extra-examples).
