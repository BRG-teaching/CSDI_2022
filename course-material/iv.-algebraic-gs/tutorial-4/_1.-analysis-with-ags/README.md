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
