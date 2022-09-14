# Exercise

{% hint style="info" %}
Complete the tasks below, and submit a zipped folder that includes the following three files by **9:00am on Friday, October 1st**.&#x20;

1. Part 1 - **Rhino file** with completed tasks
2. Part 2 - completed **Grasshopper definition**
3. Summarising **PDF**

Please follow the file naming convention as shown in the [**Syllabus**](../../syllabus.md#submissions).

### [Submit Exercise 1 here](https://www.dropbox.com/request/iMMgttjL5ZG9PBpksF3d).
{% endhint %}

## Part 1 - Graphic statics in Rhino

Complete the following 4 tasks using this Rhino file.

{% file src="../../.gitbook/assets/CSD1_exercise-1.3dm" %}

### Task 0 - Review eQUILIBRIUM drawings

eQUILIBRIUM, an interactive environment for graphic statics-based structural design, provides examples of pre-constructed graphic statics drawings. These drawings are interactive and have various features that can be used to learn various fundamental principles of graphic statics.&#x20;

For the first task of this exercise, simply check out the [first two rows of the "drawings" page on the eQUILIBRIUM platform](https://block.arch.ethz.ch/eq/drawing), and learn the principles and construction techniques demonstrated in each drawing.&#x20;

![](<../../.gitbook/assets/image (209).png>)

### Task 1 -  Resultant of two non-parallel forces

For the given loading case, find the magnitude and direction (indicate using the `ArrowHead` command in Rhino) of the resultant in the force diagram as well as its position in the form diagram. In the PDF, briefly describe the construction procedure.

![](<../../.gitbook/assets/image (197).png>)

### Task 2 - Resultant of several non-parallel forces

Find the magnitude and direction (indicate using the `ArrowHead` command in Rhino) of the resultant in the force diagram as well as its position in the form diagram by using a trial funicular. In the PDF, briefly describe the construction procedure.

![](<../../.gitbook/assets/image (240).png>)

### Task 3 - Resultant of several parallel forces

Given is a shape of stacked boxes glued together. Each acting force corresponds to the weight of one box. Find the magnitude and the direction of the resultant (indicate direction using the `ArrowHead` command in Rhino) in the force diagram as well as its position in the form diagram by using a trial funicular and check whether the arrangement is stable. In the PDF, briefly describe the construction procedure and the solution.

![](<../../.gitbook/assets/image (177).png>)

### Task 4 - Drawing subsystems

Draw a corresponding force diagram for each subsystem (a-f). Determine the magnitude \[kN] of each force and mark its direction (using the `ArrowHead` command in Rhino) in the subsystem. Indicate tension forces with red and compression forces with blue. In the PDF, briefly describe the construction procedure and the solution for each subsystem.

![](<../../.gitbook/assets/image (131).png>)

## Part 2 - Grasshopper basics

![](../../.gitbook/assets/csd1\_ex1\_balloons.png)

### Task Description

To practise your Grasshopper skills and parametric thinking, write your name initials in a parametric manner!

* Use only a single starting point, vectors and lines.&#x20;
* Build it up in a way that you can change the height, width and distance between letters, and scale it all, move it all, and rotate it all.&#x20;
* Pipe the letters to make them look balloony and colour them in a colour pattern of your choice (to practise datastructure handling).

{% hint style="danger" %}
Do not use the `Scale` component but instead scale your letters with the multiplication of your vectors!
{% endhint %}

{% hint style="success" %}
These components should be part of your script (possibly amongst others):

* [ ] Slider
* [ ] Panel
* [ ] Construct Point
* [ ] Unit Vectors and/or Vector XYZ
* [ ] Multiplication
* [ ] Division
* [ ] Rotate Vector
* [ ] Move
* [ ] Line and/or Interpolate Curve
* [ ] Merge&#x20;
* [ ] Entwine
* [ ] ... find a component yourself for the balloony look
* [ ] Weave
* [ ] Colour Swatch
* [ ] Custom Preview

All these components were introduced to you in [Tutorial 1](tutorial-1.md) step-by-step so it's a good opportunity to revise the tutorial.
{% endhint %}

### Example

This is how it looks like for the initials of CSD1: (for you 2 letters are enough)

**1.** This is how your letters should look with auxiliary points of construction and the lines/curves connecting them:

![](../../.gitbook/assets/csd1\_ex1\_points-curves.png)

**2.** This is how they should look like as balloons with a colour pattern:

![](<../../.gitbook/assets/csd1\_ex1\_balloons (1).png>)

{% hint style="info" %}
Task: What is the boolean input pattern in numbers of 0 and 1.&#x20;
{% endhint %}

**3.** This is how you should be able to change the height, width and distance of the letters:

![](../../.gitbook/assets/csd1\_ex1\_height-width-distance.gif)

**4.** This is how you should be able to change the overall position of it:

![](../../.gitbook/assets/csd1\_ex1\_position.gif)

**5.** This is how you should be able to change the overall scale of it:

![](../../.gitbook/assets/csd1\_ex1\_scaling.gif)

**6.** This is how you should be able to rotate the letters:

![](<../../.gitbook/assets/csd1\_ex1\_rotate (1).gif>)

## Part 3 -Summarising PDF

Answer the question(s) on the following document.&#x20;

{% file src="../../.gitbook/assets/CSD1_2021_exercise-1_template.docx" %}

## Solutions

### Part 1 - Graphic statics in Rhino

![](../../.gitbook/assets/JL\_UE01\_Solution-01.png)

![](../../.gitbook/assets/JL\_UE01\_Solution-02.png)

### Part 2 - Grasshopper Basics

This is one possible solution for the letters. It is not the most straightforward solution as it was meant to include all the different components and logic from the tutorial. However, it's completely fine if you solved it with a different strategy.&#x20;

{% file src="../../.gitbook/assets/ex1_gh_name.gh.zip" %}
Solution File Initial Letters in Grasshopper
{% endfile %}
