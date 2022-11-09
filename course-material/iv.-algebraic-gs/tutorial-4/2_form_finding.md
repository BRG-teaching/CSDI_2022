# 2.1. Funicular arch

The input geometry is the following circular arch:

![](<../../../../.gitbook/assets/image (238).png>)

We are going to assume that:

* The load in each node is equal to **10 kN**.
* The two extremities are pin supports (restrain on x, y).

With this example we want to check if the input geometry is suitable for a uniformilly distributed load, and if not which is the shape corresponding to such load case.

### 1. Form Diagram with loads and support

We input the FormDiagram with the function `Crerate Form Diagram` from the lines provided in the Rhino template, applied loads and reactions are translated as lines in the diagram. The result look like this:

![](<../../../../.gitbook/assets/image (224).png>)

We assign the forces with the button `Assign Forces`. This predefined shape allows the selection of only one independent edge. We select one of the edges representing the applied loads and assign the load -10. Here edge #2 was selected.

![](<../../../../.gitbook/assets/image (398).png>)

We press OK and validate the sign of the applied load, we must also restraint the two extremity vertices assigning it as supports/anchors with the button `Identify Anchors`. The result will look like the following image:

![](<../../../../.gitbook/assets/image (267).png>)

With this information updated we can go to the drawing of the Force Diagram.

### 2. Drawing of the Force Diagram

We press the button `Create Force Diagram` which generated the ForceDiagram highlighted in the following image. We observe that the force 10 kN is only applied to the edge selected as independent and the other applied loads are different to 10 kN. This happens because the original input geometry was not form found to correspond to a uniformilly distributed load. Instead we see forces varying from 10 to 24.6 kN.

![](<../../../../.gitbook/assets/image (298).png>)

If we want to find out the correct geometry of the structure for the uniformilly applied load case we must assign constraints to the problem.

### 3. Constraint the equilibrium to uniformilly distributed load

To achieve the geometry corresponding to the uniformilly distributed load from our hypothesis we first assign the default constraint by clicking in the button `Assign default constraints`. We see highlighted the constraints in **white** to the form and force diagrams as explained in the [part 2](./) of this tutorial.&#x20;

* Edges in the form and force diagrams with orientation fixed are highlighted in white.
* Vertices in the form and force diagram with line constraint are highlighted in white.
* Anchored vertices are shown in red (as the supports of the [part 1](../1.-analysis-with-ags/)).

Since white is the default color for the constraints remember to change your backgroud color. Grey is prefered. The visualisation of the arch after the default constrains should look as follows:

![](<../../../../.gitbook/assets/image (374).png>)

On top of the default constraints applied, we assign **target forces** to the load edges with the same magnitude of the applied load. This reflect as a constraint on the **target length** of the dual edges in the force diagram. To assign these additional constraints click on the button `Assign edge constraints` and select the option `ForceMagnitude`. Select all applied loads and give the target magnitude (10 kN). The sign +/- is not important here since it will always take the same sign of the applied load. The target forces will show in white in the form and force diagrams

![](<../../../../.gitbook/assets/image (412).png>)

Now, we applied constraints to the form and force diagrams which force them to look for a new equilibrium. On the next section we will perform the bi-directional update.

### 3. Bi-directional update

Before performing the bi-directional update (Form<->Force) turn on the bi-directional update in the <img src="../../../../.gitbook/assets/image (36).png" alt="" data-size="line">`Settings`. If you continue without turning it on you will receive an error message.

![](<../../../../.gitbook/assets/image (296).png>)

Now that the bi-directional module is activated you click on  <img src="../../../../.gitbook/assets/image (75).png" alt="" data-size="line">`Update Both Diagrams`. Both diagrams will update and the result should be as displayed below:

![](<../../../../.gitbook/assets/image (228).png>)

The final solution is shalower than the original input and now the geometry is a parabola instead of a circle. The differences among the two solutions are displayed below.

![](<../../../../.gitbook/assets/image (372).png>)

The constraints can be turned on and off, in the latter the original force in the edge is displayed. Aditionally in the `Inspect diagrams > ConstraintsTable` a table is called showing all constraints and the current force in the edges, as well as the constraints in the vertices applied.

![](<../../../../.gitbook/assets/image (132).png>)

The constraints can be erased from the form on the Menu function `IGS> Constraints> Remove all constraints.`

![](<../../../../.gitbook/assets/image (93).png>)

### 4. Additional modifications

If the constraints are not erased, or are reassigned more modificaitions could be done on top of the current design. We will explore two simple ones. In the first modification we move one of the supports as in the image below:

![](<../../../../.gitbook/assets/image (314).png>)

We then press in the button Update both diagrams and both diagrams are matched according to the constraints and the new support position. The resultant structure is still a funicular for the uniformelly distributed load case but with supports in different elevations which make the vertical reaction forces unbalanced: 38.3kN and 21.7 kN as shown in the next figure:

![](<../../../../.gitbook/assets/image (109).png>)

The second additional modification imposes an additional target force to one of the reaction forces. Here we set the horizontal reaction force to have magnitude of 30 kN. As a result, the funicular change its height and in the force polygon the horizontal reaction force has its length decreased. The following images show this modifications.

![](<../../../../.gitbook/assets/image (120).png>)

![](<../../../../.gitbook/assets/image (363).png>)

Many more modifications are possible and playing around with the previous unidirectional is still possible.


# 2.2. Constant Force

The last example deals with the following non-triangulated truss:

![](<../../../../.gitbook/assets/image (50).png>)

This truss was form found to a equally distributed load which we will assume here as **10 kN** at each node. We want to compute the equilibrium and generate the force diagram for this structure and perform bi-directional modifications with IGS.

### 1. Form Diagram with loads and support

We input the FormDiagram with the function `Create FormDiagram` using the lines provided in the Rhino file, applied loads and reactions are translated as lines in the diagram. The result look like this:

![](<../../../../.gitbook/assets/image (378).png>)

Now we assign loads with the button `Assign Forces`. This predefined shape allows the selection of only one independent edge. We select one of the edges representing the applied loads and assign the load **+10**. Here edge #13 was selected.

![](<../../../../.gitbook/assets/image (277).png>)

We press OK and validate the sign of the applied load, we must also restraint the two extremities vertices assigning it as supports/anchors using the button `Identify Anchors`. The result will look like the following image:

![](<../../../../.gitbook/assets/image (98).png>)

With this information updated we can go to the drawing of the Force Diagram.

### 2. Drawing of the Force Diagram

We press the button `Create Force Diagram` which generated the ForceDiagram highlighted in the following image. We observe that the force 10 kN is not only applied to the edge selected as independent but also to the other applied loads. Therefore the input geometry was already form-found to such load case. The reaction forces are ballanced on the vertical 20 kN at each support.

![](<../../../../.gitbook/assets/image (45).png>)

Anoter particularity of this solution is that the bottom chord has constant tensile force equals 31.2 kN (edges 0, 1, 5, 16, 18) while in the upper chord the forces vary from  37.1 kN (edges 20, 10) to 31.2 kN (edge 9). The following can be observed with the tools available over the `Inspect Diagrams` function, such as the `EdgesTable` shown below:

![](<../../../../.gitbook/assets/image (380).png>)

On the next section we will impose constraints to form find the truss such as the edges in the top chord have constant force equals 30 kN.

### 3. Impose constraints to the problem.

We will apply the required constraints in 4 steps:

First, the default constraints are applied affecting the leaf edges (loads and reactions) and the vertices connected to it. This can be done pressing the button `Apply Default Constraints`.

![](<../../../../.gitbook/assets/image (268).png>)

Second, we assign target forces to the top chord. In the button `Assign edge constraints` over the option `ForceMagnitude` we assign 30 kN to edges 7, 9, 10, 11, 20.

![](<../../../../.gitbook/assets/image (297).png>)

Third, multiple solutions for a constant top chord exist, in this tutorial we will intially look for the one which keep the bottom chord flat. To do that we click once more to the `Assign edge constraint` button over the option `EdgeOrientation` and select edges 0, 1, 5, 16, 18 in the bottom chord. The display should look like below:

![](<../../../../.gitbook/assets/image (124).png>)

Finally, to preserve the load case we assign target edges also to the applied loads. On the function `Assign edge constraints` option `ForceMagnitude` we assign 10 kN to the applied loads. The result look like below:

![](<../../../../.gitbook/assets/image (289).png>)

Once the constraints above are set we can go to the bi-directional update of the form and force diagrams.

### 4. Bi-directional update

To update the diagrams, we click on the button `Update both diagrams`. The result is depicted below:

![](<../../../../.gitbook/assets/image (389).png>)

On the image below we see the overlap of the initial and final solutions. The dual edges of the top chord need to be moved to a circle with radius equals 30 kN. The modifications that would have to be done manually are displayed in the next Figure:

![](<../../../../.gitbook/assets/image (76).png>)

### 5. Additional modifications

One additional modification will be performed. The top and bottom chord are constrained to the same target force 30 kN. As a consequence the bottom chord can no longer be flat. Therefore we remove that constraint and assign target edges to the bottom chord. The final state of the constraints applied should look like below:

![](<../../../../.gitbook/assets/image (252).png>)

Now, we can apply the update to form and force diagrams and the result is the double constant truss below:

![](<../../../../.gitbook/assets/image (156).png>)

### 5. Advanced visualisation

To finalise we show a few advanced visualisations available in IGS. On the settings menu the diagram can be rotated of 90 degrees. In this way when the diagrams are in equilibrium the form and force corresponding edges are perpendicular to each other instead of parallel. The figure below shows how to activate this function on the ForceObject Settings.

![](<../../../../.gitbook/assets/image (43).png>)

An extra visualisation is available with the Unified Diagram. This diagram unifies form and force diagram in the same plot. Different unified diagrams can be drawn for different values of alpha. Alpha is de parameter that changes the shape of the unified diagram to follow form or force. On the figure below you see the final example of this page with the unified diagram for different alphas. More about this topic will be studied in our last module [3D graphic statics](broken-reference).

![](<../../../../.gitbook/assets/image (29).png>)

That's it! You made the tutorial 4. If you want to learn even more dive in the [extra examples](../3.-extra-examples/).
