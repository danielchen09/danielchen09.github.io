# Log of survival game
## 6/12/2021
![0612202101](https://imgur.com/gallery/4WU9kFC)
### What worked
- Terrain generation using marching cubes
- Chunk loading and off loading
- Can render chunks at around 30 to 60 fps
- Terrain deforming
- Basic vertex colors

### Problems
- Chunk generation is slow, with render distance of 7 (7 in each octant), chunk generation in one frame could take up to ~134ms (most of the time are spent baking colliders)
- Terrain deforming speed is not consistent
- Vertex colors unnatural when transitioning to another material