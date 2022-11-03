---
description: Form-finding of funicular structures using graphic statics in Python
---

# Tutorial 2

## Learning Goals

In this tutorial, you will:

* learn how the Grasshopper algorithm from module 2 is translated to Python.
* understand the advantages that programming in Python has over creating an algorithm in Grasshopper.

{% hint style="warning" %}
The purpose of this course is to give you a brief introduction to the topic of programming but not to teach you all what is needed for you to write algorithms by yourself. For this reason, in this tutorial we will only cover the very basics of this wild field.
{% endhint %}

## Translating to Python module 2 algorithm

In the previous module we built a linear algorithm in Grasshopper for the form-finding of a two-dimensional funicular cable structure. To do this the steps we followed the same as when we build the funicular with paper and pencil: 1. Resultant, 2. Reactions and 3. Internal forces. We will now program using Python (within Grasshopper) the same algorithm following those same steps. This will allow you to learn the basics of linear programming and identify its main advantages over Grasshopper.

### 1. Input loads and resultant

{% hint style="info" %}
In this section we will create the following variables and lists:

* **Lp\_anc\_in** (List of points/anchors/initial)
* **Ln\_mag\_in** (List of numbers/magnitudes/initial)
* **Lp\_anc** (List of points/anchors)
* **Ln\_mag** (List of numbers/magnitudes)
* **Lv\_load** (List of vectors/loads)
* **Ll\_LOA** (List of lines/lines of action)
* **X** (first point load line in force diagram)
* **O1** (random pole to find resultant)
* **Lp\_loadline** (List of points/loadline)
* **Ll\_loadline** (List of lines/loadline)
* **Lal\_force** (List of auxiliary lines/force diagram)
* **p\_right** (point/right cliff)
* **Lal\_form** (List of auxiliary lines/form diagram)
* **p\_R** (point/resultant)
{% endhint %}

1.a In this step we will store all the necessary data regarding the input loads:

* First, we will first store in two lists all the initial anchor points and magnitudes (Lp\_anc\_in and Ln\_mag\_in).
* Then, we will create another two lists (Lp\_anc and Ln\_mag) where we will only store the anchor points and magnitudes if the magnitudes are different than zero.
* After, we we will create a vector (v) and a line of action (LOA) for each of the loads and we will store these in lists (Lv\_load and Ll\_LOA).

```python
import rhinoscriptsyntax as rs

#input
Lp_anc_in=[p1,p2]
Ln_mag_in=[n1,n2]

#store only the anchors and magnitudes if they are different than zero 
Lp_anc=[]
Ln_mag=[]
for i in range (0,len(Ln_mag_in)):
    if Ln_mag_in[i] !=0:
        Lp_anc.append(Lp_anc_in[i])
        Ln_mag.append(Ln_mag_in[i])

#vector loads
Lv_load=[]
for i in range (0,len(Lp_anc)):
    v=([0,Ln_mag[i],0])
    Lv_load.append(v)

#LOA (Line Of Action)
Ll_LOA=[]
for i in range (0,len(Lp_anc)):
    p=rs.CopyObject(Lp_anc[i])
    rs.MoveObject(p,[0,-10,0])
    LOA=rs.AddLine(Lp_anc[i],p)
    Ll_LOA.append(LOA)
```

1.b We now want to find out the position of the resultant in the form diagram using the trial funicular. To do this, we will build the force diagram. These are the steps:

* First, we will create the load line of the force diagram using as a starting point one point from Rhinoceros (X) and we will already store this first point in a list (Lp\_loadline).
* Then, we will make a copy a X (p), move it according to the first vector in Lv\_load and create a line representing the external force (X to p). As we want to do the same for all the external loads we will need a loop.

{% hint style="warning" %}
In order to add the loads one after another we must update the value of the starting point (X) with that of the moved point in the previous iteration (p), so at the end of the loop we must write X=p. We will store the points along the load line (Lp\_loadline) as well as the lines representing the external loads (Ll\_loadline).
{% endhint %}

* After, we will define, also in Rhinoceros, the random pole O1 and we will create using a loop the auxiliary lines connecting O1 with the points along the load line. We will store these lines in Lal\_force.

```python
import rhinoscriptsyntax as rs

#force diagram load line
Lp_loadline=[]
Lp_loadline.append(X)
Ll_loadline=[]

for i in range (0,len(Lv_load)):
    p=rs.CopyObject(X,Lv_load[i])
    l=rs.AddLine(X,p)
    Lp_loadline.append(p)
    Ll_loadline.append(l)
    X=p

#force diagram aux lines
Lal_force=[]
for i in range (0,len(Lp_loadline)):
    al=rs.AddLine(O1,Lp_loadline[i])
    Lal_force.append(al)
```

1.c And we will continue the construction of the resultant in the form diagram. These are the steps:

* First, we will define a point a long the curve of the right cliff (p\_right). We will do this in Grasshopper as the component "Point On Curve" makes it very easy.
* Then, we will copy the auxiliary lines of the force diagram, move them to the form diagram and intersect them with the lines of action of the external loads. In order to repeat these actions we will create a loop.

{% hint style="warning" %}
If you construct the resultant by hand, as shown in the tutorial of module 2, you will see that when a structure has two external loads, there are three auxiliary lines in the force diagram. When we move these three auxiliary lines to the form diagram, as there are only two loads and therefore two lines of action, we will only move and intersect the first two auxiliary lines, while for the third auxiliary line we will only move it. To achieve this we will use a conditional within the loop.
{% endhint %}

{% hint style="warning" %}
In the loops we created in the previous steps "i" was a number that we were using as the index to access items from a list. In this case however "i" are the actual items within Lal\_force. Because of this we can't write Ll\_LOA\[i]. In order to access the items within Ll\_LOA we will create an additional variable (a), we will say its initial value its 0 and at te end of the loop we will add +1 to it to allow us to access all the items.
{% endhint %}

{% hint style="warning" %}
Notice that in the loop vector v is not always the same. The first vector v goes from O1 to p\_right. However, in the next iterations of the loop, v goes from O1 to the intersection points we find. Therefore we must update the value of p\_right at the end of the loop.
{% endhint %}

* Finally, we will intersect the first and last auxiliary line in the form diagram to find the point p\_R across which the vertical line of action of the resultant goes through.

```python
import rhinoscriptsyntax as rs

Lal_form=[]
a=0
for i in Lal_force:
    if i != Lal_force[-1]:
        v=rs.VectorCreate(p_right,O1)
        al=rs.CopyObject(i,v)
        ip=rs.LineLineIntersection(al,Ll_LOA[a])
        Lal_form.append(al)
        p_right=ip[0]
        a=a+1
    else:
        p_right=ip[0]
        v=rs.VectorCreate(p_right,O1)
        al=rs.CopyObject(i,v)
        Lal_form.append(al)

p_R=rs.LineLineIntersection(Lal_form[0],Lal_form[-1])[0]
```

### 2. Reactions

{% hint style="info" %}
In this section we will create the following variables:

* **sp\_left** (support point/left cliff)
* **sp\_right** (support point/right cliff)
* **O2** (this point defines the triangular polygon of forces of the global equilibrium)
{% endhint %}

In this section we will calculate the reaction forces at the supports. These are the steps:

* First, we will define the position of the supports (sp\_left and sp\_right) along the curves of the cliffs using once again the Grasshopper component "Point On Curve".
* Then, we will create two lines in the form diagram connecting the supports with the anchor of the resultant (p\_R).
* Finally, we will move these lines from the form diagram to the force diagram and intersect them finding point O2 and closing the polygon of forces representing the global equilibrium of the structure.

```python
import rhinoscriptsyntax as rs

#creating lines of reaction forces in form diagram
l1=rs.AddLine(p_R,sp_left)
l2=rs.AddLine(p_R,sp_right)

#building reaction forces in form diagram
v1=rs.VectorCreate(Lp_loadline[-1],p_R)
l1_m=rs.MoveObject(l1,v1)

v2=rs.VectorCreate(Lp_loadline[0],p_R)
l2_m=rs.MoveObject(l2,v2)

O2=rs.LineLineIntersection(l1_m,l2_m)[0]
```

### 3. Internal forces

{% hint style="info" %}
In this section we will create the following lists:

* **Ll\_int\_force** (List of lines/internal forces/force diagram)
* **Ll\_int\_form** (List of lines/internal forces/form diagram)
* **Lip\_form** (List of points of intersection/form diagram)
{% endhint %}

In this section we will construct the funicular. Thes are the steps:

* First, we will create the lines of the internal forces in the force diagram (Ll\_int\_force) connecting O2 with Lp\_loadline.
* Then, we will construct the geometry of the funicular in the form diagram using a loop. This process is basically the same as when we constructed the trial funicular in step 1.c.

```python
import rhinoscriptsyntax as rs

#creating lines of internal forces in force diagram
Ll_int_force=[]
for i in range (0,len(Lp_loadline)):
    l=rs.AddLine(O2,Lp_loadline[i])
    Ll_int_force.append(l)

#building form diagram of funicular
Ll_int_form=[]
Lip_form=[]
a=0
for i in Ll_int_force:
    if i != Ll_int_force[-1]:
        v=rs.VectorCreate(sp_right,O2)
        l=rs.CopyObject(i,v)
        ip=rs.LineLineIntersection(l,Ll_LOA[a])
        Ll_int_form.append(l)
        Lip_form.append(ip[0])
        sp_right=ip[0]
        a=a+1
    else:
        sp_right=ip[0]
        v=rs.VectorCreate(sp_right,O2)
        l=rs.CopyObject(i,v)
        Ll_int_form.append(l)
```

### 4. Data for visualization

{% hint style="info" %}
In this section we will create the following lists:

* **Ll\_force** (List of lines/force diagram)
* **Ll\_form1** (List of lines/form diagram/the verticals)
* **Ll\_form2** (List of lines/form diagram/the actual funicular)
* **Ll\_form** (List of lines/form diagram)
{% endhint %}

In this section we will create the data for visualization according to the convention shown below, just like we did in modules 1 and 2.

![](../../.gitbook/assets/directions.jpg)

```python
import rhinoscriptsyntax as rs

#data for visualization (force diagram)
Ll_force=Ll_loadline+Ll_int_force

#data for visualization (form diagram)
Ll_form1=[]
for i in range (0,len(Lip_form)):
    l=rs.AddLine(Lip_form[i],Lp_anc[i])
    Ll_form1.append(l)

Lip_form.insert(0,sp_right)
Lip_form.append(sp_left)
Ll_form2=[]
for i in range (0,len(Lip_form)-1):
    l=rs.AddLine(Lip_form[i+1],Lip_form[i])
    Ll_form2.append(l)

Ll_form=Ll_form1+Ll_form2
```

### 5&6. Sense, force magnitude and visualization

Just like we did in module 2, we will copy\&paste "sense", "force magnitude" and "visualization" from the Grasshopper definition from module 1.

![](<../../.gitbook/assets/5&6 (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (4).jpg>)

#### You made it! :) You can now explore the design space of your parametric model!

{% file src="../../.gitbook/assets/gs_tutorial_procedural_II.zip" %}
