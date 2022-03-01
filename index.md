# Project 2 Write-Up

## Part 1

### Description and Implementation of our Algorithm
The idea of the de Casteljau's algorithm is to lerp together an arbitrary `n` points pair-wise (with a predetermined weight `t`) to generate a subsequent `n-1` points. This is done recursively until we only have `1` point and the process is then terminated. In this task, we implement one step of this process.

### Making a Curve
![](images/bezier1.png)
![](images/bezier2.png)
![](images/bezier3.png)
![](images/bezier4.png)
![](images/bezier5.png)
![](images/bezier6.png)
![](images/bezier7.png)

### Manipulating the Curve
![](images/bezier8.png)


## Part 2

### Description and Implementation of our Algorithm
The de Casteljau algorithm on a Bezier curve is to reduce `n` control points to a singular control point. The method we used to apply this algorithm to a surface is to apply this algorithm recursively to the given `nxn` points. First, we applied the algorithm to each row (each row being `n` elements) parameterized by `u`. Then we created a vector made out of these evaluated points. Then we applied our 1D evaluation algorithm on these points, parameterized by `v`. This would give you a singular point in 3D space, as desired.

### Screenshot
![](/images/teapot.png)


## Part 3

### Description and Implementation
First, we define "neighboring triangles" as all triangles that have `this` vertex as one of their vertices. We set up a half-edge traversal algorithm with this in mind, which stops implementation when we return to our original half-edge. For every half-edge, we get the associated face. For every face, we get the value of it's normal (through the Face::normal() function) and weigh it by calculating the area of the face. The area of the face is calculated by taking half the Euclidean norm of the normal. We add all these values together. Once this is complete, we normalize the resultant vector and return it.

### Comparing Teapots with Flat Shading and Phong Shading
![](/images/teapot1.png)
![](/images/teapot2.png)

## Part 4

### Description of Implementation
For edge flipping, we hunkered down and just drew out triangles with every single possible element labeled, using the picture posted in the edge flip Piazza thread as a guide. From there, we followed the recommendations in the spec to create variables for all elements and just reassign everything, regardless of whether or not the pointers should change. The `setNeighbors` function was very very helpful for keeping things compact!

### Doing Some Flips
After one flip
![](/images/flip1.png)

After several flips
![](/images/flip2.png)

### Our Debugging Journey
We had a very eventful debugging journey! Probably not a good thing, but because it was just too hard to debug individual lines based on the renderings, we wiped everything and restarted. We still ran into some issues after many many flips that were very hard to reproduce, so we tried to rubber duck each other with a whiteboard and rewrote the function one more time, which surprisingly fixed things.

## Part 5

### Implementation
We approached edge splitting very similarly to how we approached edge flipping

### Doing Some Splits
Before
![](/images/split1.png)

After
![](/images/split2.png)

### Doing Splits AND Flips
Before
![](/images/fas1.png)

After
![](/images/fas2.png)

### Debugging Journey
Like the debugging for edge flipping, we mostly just redid the whole thing at once because it was too much of a headache trying to pick apart each line. We were struggling with a strange bug that created protruding spikes in task 6, which we narrowed down to our edge splitting algorithm. Luckily, one of our friends posted their drawing of the before and after elements on the edge splitting Piazza thread, so we followed that and actually found our bugs (we were accidentally creating a few too many halfedges). After completely rewriting our function based on carefully following the drawing, we were able to fix the issue!

## Part 6
