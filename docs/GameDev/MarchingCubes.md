# Marching Cubes
## Resources
- [https://www.youtube.com/watch?v=M3iI2l0ltbE&t=73s](https://www.youtube.com/watch?v=M3iI2l0ltbE&t=73s)
- [http://paulbourke.net/geometry/polygonise/](http://paulbourke.net/geometry/polygonise/)
- [https://developer.nvidia.com/gpugems/gpugems3/part-i-geometry/chapter-1-generating-complex-procedural-terrains-using-gpu](https://developer.nvidia.com/gpugems/gpugems3/part-i-geometry/chapter-1-generating-complex-procedural-terrains-using-gpu)

## 3D perlin noise
- [https://gist.githubusercontent.com/tntmeijs/6a3b4587ff7d38a6fa63e13f9d0ac46d/raw/f0133f4c794399641564da6c722faee445153206/unitythreedimensionalperlinnoise.cs](https://gist.githubusercontent.com/tntmeijs/6a3b4587ff7d38a6fa63e13f9d0ac46d/raw/f0133f4c794399641564da6c722faee445153206/unitythreedimensionalperlinnoise.cs)
```c#
private static float Noise3D(float x, 
                             float y, 
                             float z, 
                             float frequency, 
                             float amplitude, 
                             float persistence, 
                             int octave, 
                             int seed) {
    float noise = 0.0f;

    for (int i = 0; i < octave; ++i) {
        // Get all permutations of noise for each individual axis
        float noiseXY = Mathf.PerlinNoise(
            x * frequency + seed, 
            y * frequency + seed) * amplitude;
        float noiseXZ = Mathf.PerlinNoise(
            x * frequency + seed, 
            z * frequency + seed) * amplitude;
        float noiseYZ = Mathf.PerlinNoise(
            y * frequency + seed, 
            z * frequency + seed) * amplitude;

        // Reverse of the permutations of noise for each individual axis
        float noiseYX = Mathf.PerlinNoise(
            y * frequency + seed, 
            x * frequency + seed) * amplitude;
        float noiseZX = Mathf.PerlinNoise(
            z * frequency + seed, 
            x * frequency + seed) * amplitude;
        float noiseZY = Mathf.PerlinNoise(
            z * frequency + seed, 
            y * frequency + seed) * amplitude;

        // Use the average of the noise functions
        noise += (noiseXY + noiseXZ + noiseYZ + noiseYX + noiseZX + noiseZY) / 6.0f;

        amplitude *= persistence;
        frequency *= 2.0f;
    }

    // Use the average of all octaves
    return noise / octave;
}
```
- (https://gist.githubusercontent.com/jstanden/1489447/raw/d84374044aa0f75d0f144904fcbe76b5927e988f/gistfile1.cs)[https://gist.githubusercontent.com/jstanden/1489447/raw/d84374044aa0f75d0f144904fcbe76b5927e988f/gistfile1.cs]

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