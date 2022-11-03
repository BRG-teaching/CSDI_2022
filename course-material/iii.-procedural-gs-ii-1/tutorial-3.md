---
description: Python programming
---

# Tutorial 1

## Learning Goals

In this tutorial, you will learn the basics of linear programming in Python.

{% hint style="warning" %}
The purpose of this course is to give you a brief introduction to the topic of programming but not to teach you all what is needed for you to write algorithms by yourself. For this reason, in this tutorial we will only cover the very basics of this wild field.
{% endhint %}

## Python

Python is one of the most popular programming languages. In this course we will use Grasshopper Python to be able to program within Grasshopper. This tutorial will look only at the most most elementary items of Python: variables and lists, and flow control structures: step by step execution, conditionals and loops.

### 1. Items

#### 1.1. Variables

Variables are containers of data values. In this tutorial we are going to see only the most common variable types: **strings**, which are text, and **numbers**, which can either be integers or decimals (floats). Let's look at an example of these:

```python
#VARIABLES

#Strings
a="hello"
print a

#Numbers
a=3
b=5
print a + b
```

Output:

```
hello
8
```

#### 1.2. Lists

Lists are a type of data structure that allows you to store items. Lists have the following characteristics:

* Lists can store objects, values and also other lists.
* Items are stored in a sequence.
* Items can be accessed by their index.
* Lists can be modified along your algorithm.

Below you will find implementation of lists showing only the most basic features:

```python
#LISTS

#creating a list with for items
L_1=[5,9,4,1]
print L_1

#print the first item in the list
print L_1[0]

#print the last item in the list
print L_1[-1]

#add one more item at the end of the list
L_1.append(3)
print L_1

#add one more item at a specific location in the list
L_1.insert(0,2)
print L_1

#remove one specific item from a list
L_1.remove(9)
print L_1

#check the length of a list
print len(L_1)

#reverse list
L_1.reverse()
print L_1

#add too lists
L_1= [3,1,0,7]
L_2= [8,2,0,2]
print L_1 + L_2

#Lists within lists
L_1=[[5,3],[3,-1],[7,6]]
print L_1[0]
print L_1[0][1]
print L_1[1][1]
```

Output:

```
[5, 9, 4, 1]
5
1
[5, 9, 4, 1, 3]
[2, 5, 9, 4, 1, 3]
[2, 5, 4, 1, 3]
5
[3, 1, 4, 5, 2]
[3, 1, 0, 7, 8, 2, 0, 2]
[5, 3]
3
-1
```

{% hint style="info" %}
In this tutorial the only type of data structure we will learn are lists. However, if you are interested in learning more about data structures, check tuples, sets and dictionaries.
{% endhint %}

### 2. Flow control

One crucial aspect of programming is to learn to control the execution flow. In this section we will look at the default execution flow, often referred to as "sequential", and two flow control statements: conditionals and loops.

#### 2.1. Sequential

Sequential execution is the most simple and common structure. In sequential execution the computer executes every single line of code one after another as shown in the example below.

```python
#SEQUENTIAL EXECUTION

L=[]
a=3
b=7
c=a+b
L.append(a)
L.append(b)
L.append(c)
print L
```

Output:

```
[3, 7, 10]
```

#### 2.2 Conditionals

As the name suggests in conditionals we will define a condition. If the condition is met the computer will execute one specific part of the code (if statement). We can also use conditionals to execute one specific part of the code if the condition is met or another part of the code if this condition is not met (if else statement). Moreover, one conditional can also be nested within another. Let's implement one example for each of the most common types of conditionals.

```python
#CONDITIONALS

#"if" statement
a=3
if a>2:
    b=1
print b

#"if else" statement
a=3
if a<2:
    b=1
else:
    b=3
print b

#"elif" statement (when there are more than two possibilities)
a=0
if a>0:
    b=1
elif a<0:
    b=3
elif a==0:
    b=10
print b

#nested conditionals
a=3
b=5
if a>=3:
    if b==4:
        print a+b
    else:
        print a-b
        
        
```

Output:

```
1
3
10
-2
```

#### 2.3 Loops

Loops (often called "for" loops) allow you to execute multiple times a series of instructions. The example below shows the implementation of a common loop structure.

```python
#LOOPS

#print 3 times the word "hello"
for i in range (0,3):
    print "hello"

#print the value of "i" along the loop (you get 5 values starting from 0)
for i in range (0,5):
    print i

#And now store in a list the value of "i" along the loop
L=[]
for i in range (0,5):
    L.append(i)
print L

#print all the items of a list one after another (solution 1)
L=[3,6,2,1]
for i in L:
    print i

#print all the items of a list one after another (solution 2)
L=[3,6,2,1]
for i in range (0,len(L)):
    print L[i]

#add +2 to each of the numbers of a list and store these in a second list
L_1=[3,6,2,1]
L_2=[]
for i in range (0,len(L_1)):
    L_2.append(L_1[i]+2)
print L_2

#loop with an additional variable
L_a=[]
a=1
for i in range (0,4):
    L_a.append(a)
    a=a*5
print L_a

#loop with a conditional: separate items from a list in three lists
L=[3,6,-1,3,-5,7,0,3,-3,-3,-1,2,1,0]
L_positive=[]
L_negative=[]
L_zero=[]
for i in range (0,len(L)):
    if L[i]>0:
        L_positive.append(L[i])
    elif L[i]<0:
        L_negative.append(L[i])
    elif L[i]==0:
        L_zero.append(L[i])
print L_positive
print L_negative
print L_zero
```

Output:

```
hello
hello
hello
0
1
2
3
4
[0, 1, 2, 3, 4]
3
6
2
3
6
2
[5, 8, 4]
[1, 5, 25, 125]
[3, 6, 3, 7, 3, 2, 1]
[-1, -5, -3, -3, -1]
[0, 0]
```

### 3. RhinoScriptSyntax

RhinoScriptSyntax is a library of functions that allows us to execute many of the common commands in Rhinoceros. Luckily, this is installed by default in Grasshopper Python. In the example below only the most usual functions are shown. However, feel free to explore other functions by yourself. In this [link](https://developer.rhino3d.com/api/RhinoScriptSyntax/) you can find the complete list of functions.

In order to run one of the functions from the library, we will type "rs." and the name of the function, which we can find in a drop-down list. After selecting the function from the list, we will open a parenthesis and in this moment some information will appear indicating us the sort of data the function needs to work. The example below shows how to run the most common RhinoScriptSyntax functions.

#### 3.1 Creating points, lines and vectors

```python
#RhynoScriptSyntax
import rhinoscriptsyntax as rs

#Create a point
a=rs.AddPoint([10,0,0])
print a

#Create a line
a=rs.AddPoint([10,0,0])
b=rs.AddPoint([0,10,0])
line=rs.AddLine(a,b)
print line

#Create a vector between two points, from point b to point a
a=rs.AddPoint([0,0,0])
b=rs.AddPoint([10,0,0])
vec=rs.VectorCreate(a,b)
print vec
```

Output:

```
227d4db7-8d66-4cab-94ed-9460121b88fc
870bdfb6-8851-4349-be34-6eea69c9ec2e
-10,0,0
```

{% hint style="info" %}
These very long codes with numbers and letters in the output are the object ID. Python creates new ID everytime you run the code so do not get surprised if you don't get this exact number when you run the code.
{% endhint %}

#### 3.2 Basic point and line functions

```python
#RhynoScriptSyntax
import rhinoscriptsyntax as rs

#Find the coordinates of a point
a=rs.AddPoint([10,0,0])
p_coor=rs.PointCoordinates(a)
print p_coor

#Find the length of a curve
a=rs.AddPoint([10,0,0])
b=rs.AddPoint([0,10,0])
line=rs.AddLine(a,b)
line_length=rs.CurveLength(line)
print line_length

# Start and ending point of a curve
a=rs.AddPoint([10,0,0])
b=rs.AddPoint([0,10,0])
line=rs.AddLine(a,b)
line_sp=rs.CurveStartPoint(line)
line_ep=rs.CurveEndPoint(line)
print line_sp
print line_ep

#Midpoint of a curve
a=rs.AddPoint([10,0,0])
b=rs.AddPoint([0,10,0])
line=rs.AddLine(a,b)
line_mp=rs.CurveMidPoint(line)
print line_mp

#Divide a curve in 4 segments
a=rs.AddPoint([10,0,0])
b=rs.AddPoint([0,10,0])
line=rs.AddLine(a,b)
L_p_line=rs.DivideCurve(line,4)
print L_p_line
print L_p_line[1]

#Intersection between two lines
a=rs.AddPoint([10,0,0])
b=rs.AddPoint([0,10,0])
c=rs.AddPoint([0,0,10])
line1=rs.AddLine(a,b)
line2=rs.AddLine(b,c)
p_int=rs.LineLineIntersection(line1,line2)
print p_int
print p_int[0]
```

Output:

```
10,0,0
14.1421356237
10,0,0
0,10,0
5,5,0
[<Rhino.Geometry.Point3d object at 0x00000000000003CD [10,0,0]>, <Rhino.Geometry.Point3d object at 0x00000000000003CE [7.5,2.5,0]>, <Rhino.Geometry.Point3d object at 0x00000000000003CF [5,5,0]>, <Rhino.Geometry.Point3d object at 0x00000000000003D0 [2.5,7.5,0]>, <Rhino.Geometry.Point3d object at 0x00000000000003D1 [0,10,0]>]
7.5,2.5,0
(<Rhino.Geometry.Point3d object at 0x00000000000003D2 [0,10,0]>, <Rhino.Geometry.Point3d object at 0x00000000000003D3 [0,10,0]>)
0,10,0
```

#### 3.3 Basic transformation functions

```python
#RhynoScriptSyntax
import rhinoscriptsyntax as rs

#Move an object along a vector
a=rs.AddPoint([10,0,0])
vec=[5,0,0]
a_mov= rs.MoveObject(a,vec)
print rs.PointCoordinates(a_mov)

#Copy an object
a=rs.AddPoint([10,0,0])
a_copy=rs.CopyObject(a)
print a
print a_copy

#Copy and move an object along a vector
a=rs.AddPoint([10,0,0])
vec=[8,8,0]
a_copy=rs.CopyObject(a,vec)
print rs.PointCoordinates(a_copy)

#Rotate object around an axis
a=rs.AddPoint([10,0,0])
rs.RotateObject(a,[0,0,0],90)
print rs.PointCoordinates(a)

#Scale an object
a=rs.AddPoint([1,0,0])
b=rs.AddPoint([0,1,0])
line=rs.AddLine(a,b)
line_sp=rs.CurveStartPoint(line)
line_scale=rs.ScaleObject(line,line_sp,[10,10,10])
print rs.CurveLength(line_scale)
```

Output:

```
15,0,0
cf7cff22-7a0f-42bc-b1b8-68c8344d7093
3eefe542-e8c7-4870-a8bf-c9aeb2421d1a
18,8,0
0,10,0
14.1421356237
```

