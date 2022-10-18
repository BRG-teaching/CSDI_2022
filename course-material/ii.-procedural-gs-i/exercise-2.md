# Exercise

{% hint style="warning" %}
Complete the tasks below, and submit **by 9:00am on Friday, October 14th one zipped folder** that includes:

1. the Grasshopper definition file (only one file!)
2. and the PDF

Please follow the file naming convention as shown in the [**Syllabus**](../../syllabus.md#submissions).

### ****[**Submit here**](https://polybox.ethz.ch/index.php/s/BA60XLsuQJdpWuj)**.**
{% endhint %}

## Tasks

Complete the following five tasks.

{% hint style="info" %}
Use the Rhinoceros file from the tutorial as a base to solve the tasks. You can also use the Grasshopper file from the tutorial as a starting point or simply solve the tasks from scratch. Then, answer the questions in the docx file. You will find all these files [**here**](./#files).&#x20;
{% endhint %}

### 1. Control of force diagram for single-node bridge

In the tutorial, we saw how to create an interactive graphic statics model of a single-node bridge spanning over a canyon with interactive control of the **form diagram.** Now, in the exercise, the task is to modify the definition to allow for the **interactive control** of the **force diagram.**

Implement the interactive **force** control in your Grasshopper definition!

{% hint style="info" %}
This means that instead of defining the lines of action as directions through the form diagram, the lines of actions are determined through the modification of the force diagram which thus dictates the form diagram: the point can be dragged in the force diagram and thus the form diagram adapts accordingly (see video below).
{% endhint %}

![](../../.gitbook/assets/aim\_exercise\_1\_fast4.gif)

### 2. Limitation of force magnitudes

A geotechnical engineer examined the cliffs of the canyon and thus dictates that they can support a **maximum force of 12kN**.

_Implement the limit of the support forces **graphically** in your force diagram with a **warning** symbol in your Grasshopper definition!_

{% hint style="danger" %}
**The solution must be graphical.** Mathematical checks with the `<` component checking if the value of the force magnitude is below the threshold will not be graded!
{% endhint %}

### 3. Single-sided bridge

The construction company states that the left cliff is much more accessible than the right cliff and therefore design options are to be explored, where **both** the left and the right elements connect **only to the left cliff**.‌

_Implement this **single-sided** bridge in your Grasshopper definition!_

{% hint style="info" %}
Think of the two mixed-tension-and-compression basic nodal configurations and how these could be rotated.
{% endhint %}

### 4. Check for fractured rocks

Further, the geotechnical engineer identified **regions** of **fractured rocks**, where it is not possible to anchor the cables.&#x20;

_Implement a **warning display** if the anchors are in the fractured region in your Grasshopper definition!_

![](../../.gitbook/assets/aim\_exercise\_2\_fast4.gif)

### 5. Favourite designs

Find two existing bridge structures that can be simplified to a single-node structure as references. Then, design your favourite bridge configurations. These designs must respect both **form and force constraints** of the limited force magnitudes of 12kN from Task 2 and the fractured rocks from Task 4. (They can be either single-sided or both-sided).\\

## Deliverables

{% hint style="success" %}
For the Exercise use the **downloaded** completed Grasshopper file from the Tutorial as a **starting point** (you can find it at the top of this page).
{% endhint %}

1. Grasshopper definition of the solutions in **one** gh-file.\
   _The definition must be **clean**, nicely grouped, labelled, and with appropriate wire display._\
   _**Highlight** your modifications in your Grasshopper definition._
2. The Pdf-Document with your answers and screenshots.\
   _The **formatting** must be kept **clean** and the **word limits** must be respected!_

## Useful components

To verify if a point is contained in one or multiple closed curves, the `Point in Curves` component is useful. If the point is outside, coincident (on the boundary), or inside the curve, the relationship output will be 0, 1, or 2, respectively. If the containment of multiple curves should be tested, the list of curves must be grafted, so that the point is tested for each curve. The output must then be flattened again. You might also need the `Mass Addition` component.

![](<../../.gitbook/assets/image (48).png>)

To display a warning at a certain condition/location, the `Symbol Display` component is useful. As input, it requires a location as a point and display settings from the `Symbol (Simple)` component. To modify the symbol style, size or colour, right-click on the input parameters of the component.

![](<../../.gitbook/assets/image (169).png>)

Further, the `Curve | Curve` component will be useful to find the intersection of two curves. Almost all other components required to solve the tasks should be familiar from the tutorials.



