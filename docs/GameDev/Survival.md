# Log of survival game
## 6/12/2021
<blockquote class="imgur-embed-pub" lang="en" data-id="4WU9kFC"  ><a href="//imgur.com/4WU9kFC">MarchingCubes-0612022101</a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

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

## 6/25/2021
![img](Images/2021062501.png)

### What worked
- Biomes
- Generation of entities like trees and cactuses

### Problems
![img](Images/2021062502.png)
- trees can sometimes spawn underground. This is caused by a volume being cut off horizontally by a chunk border, so the ray cast is able to hit what is below the surface

![img](Images/2021062503.png)
- Biome generation can be improved. Snow biome can generate in the middle of a desert.