# Modeling in Blender
## Tree
1. Edit mode (tab)
2. Select all (A)
3. Merge (alt+M, at center)
4. Extrude at vertex (E)
5. Add skin modifier
6. Scale down end branches (ctrl+A)
7. Object mode
8. Add subdivision surface modifier
    - To add a point in the middle of two points, select the two points and press (W) for subdivide
9. Object Mode (tab)
10. Apply skin modifier
11. Apply subdivision surface modifier
12. Add and apply decimate modifier for low poly effect
13. Add an Icosphere for leaves
14. Sculp mode to modify the icosphere
15. Duplicate leaves
16. Combine the leaves (ctrl+J)

## Cactus
1. Make a cactus body (cylinder for long ones and icospheres for round ones)
2. Make a single spike by scaling a cone (S)
3. Select the cactus body
4. Add a particle system (under modifiers)
5. Go to particle properties (below modifiers tab)
6. Select Hair
7. Under Render, select "Render As Object"
8. Choose the cone as the instance object
9. Check Object Rotation
10. Rotate the cone until it aligns properly (R)
11. Under modifiers, click Convert
12. Combine the spikes