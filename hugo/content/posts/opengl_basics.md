+++ draft = false date = 2018-12-04T13:07:53+08:00 title = "OpenGL Basics" slug = "" tags = [] categories = [] +++

## Vertex shader & fragment shader

> A helpful way of thinking about the difference between shaders that deal
with vertices and fragment shaders is: vertex shading (including tessellation
and geometry shading) determine where on the screen a primitive is,
while fragment shading uses that information to determine what color
that fragment will be.

**OpenGL Programming Guide,Eighth Edition**  p13


## Bind & edit approach

> Generally speaking, you will bind
an object in two situations: initially when you create and initialize the data
it will hold; and then every time you want to use it, and it’s not currently
bound. 

**OpenGL Programming Guide,Eighth Edition**  p18
