# Transvoxel
The Transvoxel Algorithm is a method for seamlessly stitching together neighboring triangle meshes generated from voxel data at differing resolutions so that level of detail (LOD) can be used with large voxel-based datasets such as volumetric terrain in next-generation video games. ([transvoxel.org](transvoxel.org))

## The problem
Stiching together meshes generated with different resolutions can result in holes

## Voxel Data
Voxel data is assumed to be an integer in [-127, 127]

## Modified marching cubes
- Like the original marching cubes algorithm, the modified marching cubes algorithm loop through every 2x2 voxel (a cube) and generate triangles
- The corners of a cube is labeled the same way as the original marching cubes
![Cube Corners](./Images/CubeCorners.png)
- 