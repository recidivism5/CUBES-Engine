Requires:
* SDL2
* GLEW

Comes with functions for:
  * Quaternion rotation
  * View matrix generation with lookAt (own implementation, not from GLM)
  * Perspective projection matrix generation
  * DDS texture loading (Credit to tilkinsc on github, the dds loader is entirely his: https://gist.github.com/tilkinsc/13191c0c1e5d6b25fbe79bbd2288a673)
  * Mouse camera rotation
  * WASD noclip movement

The shaders, which are all copied directly from opengl-tutorial.org, form the core of this engine. Whenever you want to render something, you'll need a big long 1 dimensional array of vertices. 3 consecutive values make a vertex.

The current state has a bunch of mario judah cubes rotating around so you can mess around with those to see how they get textured. To map textures, you just need a big 1-dimensional array of UV coordinates, 2 for each vertex in whatever mesh you are trying to render.

Anyways to render geometry in a different place/orientation/scale you gotta alter your final matrix that gets passed in to the MVP slot in the vertex shader. That is, unless you want to make a different system like a vertex shader that first multiplies
each vector by a rotation/translation matrix and then by your MVP matrix or really whatever on earth you want! INFINITE WAYS TO TRANSFORM YOUR SHAPES AND PROJECT THEM! YEAAH!!!!

I think a cool hack might be to make a new quaternion rotator that just multiplies your point by one quaternion, instead of sandwiching it between two. You could experiment with 4d transformations and projections.
