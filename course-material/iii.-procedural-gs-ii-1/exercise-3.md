# Exercise 2

{% hint style="warning" %}
Complete the tasks below, and submit **by 9:00am on Friday, November 18th one zipped folder** that includes:

1. the Rhinoceros file.
2. the Grasshopper definition file (one algorithm per task but all in one single Grasshopper file!).
3. The completed questionnaire (PDF).

Please follow the file naming convention as shown in the [**Syllabus**](../../syllabus.md#submissions).

### **Submit here**
{% endhint %}

## Tasks

Complete the following six tasks.&#x20;

{% hint style="info" %}
Use the Grasshopper file from the tutorial and the new Rhinoceros file (the one for the exercise) as a base to solve this exercise. Then, answer the questions in the docx file. You will find all these files [**here**](../iii.-procedural-gs-ii/#files).&#x20;
{% endhint %}

### 1. Add more loads

Add multiple external loads to the current algorithm.

### 2. Remove "zero" loads

The current algorithm crashes when the external loads have zero magnitude. Modify the algorithm so that when an external load has zero magnitude that load is not considered during the form-finding process.&#x20;

{% hint style="info" %}
Use the solution from Task 1 as a base to solve this task.&#x20;
{% endhint %}

### 3. Add an asymmetric load

A large group of people is crossing together the bridge. Add to the algorithm this asymmetric load and display it as if it would be moving from one anchor point to the other as shown in the video below. &#x20;

{% hint style="info" %}
Use the solution from Task 2 as a base to solve this task.&#x20;
{% endhint %}

{% hint style="success" %}
Hint:&#x20;

Use a number slider in Grasshopper to change the anchor point of the asymmetric load.&#x20;
{% endhint %}

### 4. Constrain the force diagram

Constrain the design space to those funiculars in compression whose horizontal thrust is smaller or equal to 50 kN.

{% hint style="info" %}
Use the solution from Tasks 2 as a base to solve this task.&#x20;
{% endhint %}

### 5. Compact algorithm

The algorithm from the tutorial is built up in sections. Put it now all together in a single Python component.

{% hint style="info" %}
Use the solution from Tasks 2 as a base to solve this task.
{% endhint %}

### 6. Golden Gate bridge

Using the algorithm from Task 5 as a base, create the structure below.&#x20;

{% hint style="success" %}
Hints:&#x20;

* Use three times the compact algorithm from Task 5 to build the three sections of the bridge.
* Start with the section on the right. Then, create the central section and finally the section in the left.&#x20;
* Chain the force diagrams using the last point of the loadline of one force diagram as the first point for the next one.
* In addition to the three Python components (one per section), you will have to creat a forth component&#x20;
{% endhint %}











