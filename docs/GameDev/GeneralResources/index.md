# Miscellaneous
## Table of Contents
- [Gizmos](##Gizmos)
- [Custom Inspector](##Custom-Inspector)

## Gizmos
### Basics
- Only used in editor
- Good practice to not include in build
    - Surround with
    ```c#
    #if UNITY_EDITOR
    private void OnDrawGizmos() {
        ...
    }
    #endif
    ```
    - Or put the code into an Editor folder

## Custom Inspector
- https://www.youtube.com/watch?v=RInUu1_8aGw
### Basics
- Extends `Editor`
- Apply to a class using the attribute
```C#
[CustomEditor(typeof(<class name>))]
```
- Modifications to the editor happens inside `void OnInspectorGUI()`
    - call `base.OnInspectorGUI()` first if want default GUI elements
- `target` references the object currently inspected (need a cast)

### Layout
- `GUILayout.BeginHorizontal()` and `GUILayout.EndHorizontal()`
    - GUI elements in between these functions will be laid out horizontally

### GUI elements
### Label
```C#
GUILayout.Label("Label Text");
```

### Button
```C#
if (GUILayout.Button("Button Name")) {
    // Do something
}
```

### Slider
```C#
val = EditorGUILayout.Slider("Name", displayVal, min, max);
```