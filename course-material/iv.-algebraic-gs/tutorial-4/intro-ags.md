# Lecture

## Motivation for Algebraic Graphic Statics

Procedure graphic statics has shown us that graphic statics can be a powerful tool in architecture, allowing the exploration of different forms in equilibrium by modifying two diagrams: **form** (representing the frame structure) and **force** (representing the equilibrium on the nodes). By following procedural rules one the equilibrium can be verified and the force diagram is drawn.

![Fibure 1: Procedure vs. Algebraic Graphic statics construction](<../../../.gitbook/assets/image (140).png>)

So far we have worked with single-node and funicular arch constructions. These can be dealt and programmed easily since they are composed of a few nodes and bars. The figure below illustrates the graphic statics construction for a triangulated structure (a Howe truss), which steps can be seen [here](https://block.arch.ethz.ch/eq/drawing/view/38). A much more extensive, and tedious procedure needs to be applied to construct form and force diagrams for this structure, and draw its force polygon.

![Figure 2: Procedural construction of a triangulated truss.](<../../../.gitbook/assets/image (334).png>)

Now, we introduce Algebraic Graph Statics (AGS) a method to encode the graphical information from GS in an algebraic description. The graphical link between the form and force diagrams (i.e. the diagrams need to be reciprocal) can be translated algebraically using the mathematical description for graphs.

The algorithm environment developed with AGS allows to perform the same modifications for form and force from previous lectures automatically, since the two diagrams are embedded in the data structure generated in AGS. The general workflow is described:

![](<../../../.gitbook/assets/image (146).png>)

## IGS - Interactive Graphic Statics

IGS is a graphic-statics plugin for Rhino based on Algebraic Graphic Statics, developed with the open-source framework COMPAS. The installation can be done according to the instructions [here](broken-reference/).

The main elements of the general workflow are available in the toolbar and listed here:

![](<../../../.gitbook/assets/image (333).png>)

### 0. Initialisation

Before start working with IGS the plug-in needs to be initialised. Also functions to save and load session .igs files are available.

### 1. Create Form Diagram

The form diagram represents the members of a two-dimensional structure. These members carry axial forces (compression and tension). A particularity of IGS is that forces and reactions need to be drawn as edges in the diagrams. Hence, the diagram must be composed of **internal edges** and **leaf edges**. The former represents the internal members of the structure and the latter the imposed loads and reaction forces.

### 2. Assign Forces and Supports

Following, forces should be assigned to the structure. However, they can not be selected freely to all mebers. The number of edges to select corresponds to the degree-of-freedom of the initial form diagram. These edges are called **independent edges** and the button `Check DOF` can give you information about how many edges must be selected. Supports can also be assigned to vertices of the diagram.

### 3. Compute Force Diagram

The force diagram represents the equilibrium of the nodes in the form diagram. Both diagrams are reciprocal. This means that they have the same number of edges and each edge in the form diagram corresponds to a reciprocal edge in the force diagram. Besides, these edges are parallel, and the length of the edge in the force diagram corresponds to the magnitude of the force in the form diagram. Also, each vertice in the form diagram is represented by a closed polygon in the force diagram, that represents the equilibrium in that node. Similarly, each polygon in the form diagram can be represented by a vertex in the force diagram.

### 4. Unidirectonal Update

* **Modify Form Diagram:** Modifying the geometry of the structure, after forces are assigned and a first force diagram is computed, allows to study how different geometries will modify the equilibrium.
* **Modify Force Diagram:** The equilibrium can also be modified inversely. A modification can be performed in the force diagram, inducing a change in the form diagram. This can be used to form find structures for specific force constraints, or force intents.

### 5. Constraints and bi-directional Update

IGS also allows for automatic modifications of the form and force diagram based on user-assigned constraints. These constraints can be applied to the edges or vertices of the diagram.

* **Edge constraints:** allow to constraint the magnitude of the forces, and/or their orientation. These constraints are assigned to the form diagram and are reflected to the force diagram.
* **Vertex constraints:** allow to constraint vertices to remain in a line, or constraint the vertices to be fixed (supports). Can be assigned to both diagrams.

It is important to know that the bi-directional solver is interative and will try to respect at most the constraints. However, the set of constraints must be feasible and therefore it is important to select them carefully.

### 6. Structual information

Inspectors are available to get information about the forces within the structure and the constraints that are applied. Aditionally a measure of the efficiency/volume of material required to build the structure is given with the measure of the Loadpath.

### 7. Visualisation

The diagrams can have their display settings modified to serve specific purposes.

## IGS User Interface (UI) <a href="#rhinogs-user-interface-ui" id="rhinogs-user-interface-ui"></a>

There are three ways of accessing the functions and features of IGS:

* IGS dropdown menu (all functionalities and features available)\*
* IGS toolbar (most functionalities and features available)\*
* IGS list of commands (all functionalities and features available)

\*Note that the menu and toolbar are only available for IGS on Windows.

### 1. IGS Menu <a href="#1-rv2-menu" id="1-rv2-menu"></a>

The IGS menu is organised in the sequential order of the workflow steps. The IGS menu includes all available functions and features of IGS, and it is deepicted below:

![](<../../../.gitbook/assets/image (397).png>)

### 2. IGS Toolbar <a href="#2-rv2-toolbar" id="2-rv2-toolbar"></a>

The IGS toolbar is also organised in the sequential order of the workflow steps. The IGS toolbar includes most of the available functions and features of the plugin.

![](<../../../.gitbook/assets/image (10).png>)

### 3. IGS list of commands <a href="#2-rv2-toolbar" id="2-rv2-toolbar"></a>

The list of all commands of IGS (present in the toolbar or in the menu) is presented below. The list is up to date with v. 0.3.2:

![](<../../../.gitbook/assets/image (11).png>)

## References <a href="#references" id="references"></a>

{% embed url="https://www.block.arch.ethz.ch/brg/publications/413" %}

{% embed url="https://www.block.arch.ethz.ch/brg/publications/1110" %}
