# Marching Cubes
## Resources
- [Coding Adventure: Marching Cubes](https://www.youtube.com/watch?v=M3iI2l0ltbE&t=73s)
- [Polygonising a scalar field](http://paulbourke.net/geometry/polygonise/)
- [Generating Complex Procedural Terrains Using the GPU](https://developer.nvidia.com/gpugems/gpugems3/part-i-geometry/chapter-1-generating-complex-procedural-terrains-using-gpu)

## 3D perlin noise
### Sources
- [Introduction to noise generation](http://libnoise.sourceforge.net/glossary/)

## Mesh Generation
- A mesh is composed of triangles, stored as a 1-D array
    - each group of 3 numbers is treated a a triangle
- To add an object with a mesh:
    - MeshFilter component: stores mesh information
    - MeshRenderer component: renders the mesh
- To generate a mesh:

```c#
Mesh mesh = new Mesh();
Vector3[] vertices;
int[] triangles

GetComponent<MeshFilter>().mesh = mesh;
CreateShape(vertices, triangles);
mesh.Clear();
mesh.vertices = vertices;
mesh.triangles = triangles;
```

## The Marching Cubes algorithm