# 2. Bi-directional GS

**Learning goal:** Learn how to apply constraints to the form and force diagrams to apply **topological** and **geometrical modifications** to both diagrams.

## 1. Introducing constraints

In the first part of this tutorial we studied uni-directional modifications:

* **Form -> Force:** Modifying nodes in the Form Diagram and update the Force Diagram.
* **Form <- Force:** Modifying the Force Diagram and update the Form Diagram.

These modifications need the complete drawing of the new controlling diagram, which is challenging specially for the second modifications (Form<-Force) where drawing the new force diagram is not straight-forward. In this section we add new constraints that can be applied to both diagrams and this will allow the update of both diagrams to be performed automatically from imposed constraints.

* **Form<->Force:** Both diagrams change based on the constraints applied.

Four types of constraints are possible in the current version of IGS:&#x20;

1. **Anchor a vertex**, fixing its x, y coordinates;
2. Constraint a vertex to a **line of action**;
3. Constraint **edge direction**; and&#x20;
4. Apply **target forces** in the form diagram which reflect in target lengths in the force diagram.

A general illustration of these constraints is shown below:

![](<../../../../.gitbook/assets/image (408).png>)

## 2. Default constraints

Some default constraints can be assigned with a special function in IGS. They reflect the assumptions that are implicit when doing graphic statics by hand. These are:

{% hint style="success" %}
On the form diagram:

* the vertices in the form diagram with an externally applied load are constrained to remain on the line of action of the load;
* the leaf-edges (reactions or loads) have their orientation fixed.
{% endhint %}

The image below illustrate these constraints:

![](<../../../../.gitbook/assets/image (392).png>)

{% hint style="success" %}
On the force diagram:

* edges where the dual has fixed orientation also get assigned fixed orientation;
* vertices on the extremities of applied loads must remain in the load line; and
* dual of the independent edges have the two extrmities fixed.
{% endhint %}

![](<../../../../.gitbook/assets/image (253).png>)

Now, lets dive into some examples:

## 4. Funicular arch

The first example is the form-finding of a funicular arch in compression. To access the tutorial click [here](2.1.-funicular-arch.md).

![](<../../../../.gitbook/assets/image (359).png>)

## 5. Constant Force Truss

The second example deals with a constant force truss. To access the tutorial click [here](2.2.-constant-force.md).

![](<../../../../.gitbook/assets/image (280).png>)
