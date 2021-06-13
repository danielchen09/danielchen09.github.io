# Compute Shaders

## Basics
### Define the main function
```
#pragma kernel <name of the main function>
```

### Define number of threads per group
```
[numthreads(x, y, z)]
```

### The main function
```
void <name>(uint3 id : SV_DispatchThreadID)
```

## Compute Buffers
