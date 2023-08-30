# Mirror Object In Unity

## Imp
`Assets/Editor/MirrorObjectsEditor.cs`
```c++
using UnityEngine;
using UnityEditor;

[CustomEditor(typeof(MirrorObjectsTool))]
public class MirrorObjectsEditor : Editor
{
    public override void OnInspectorGUI()
    {
        base.OnInspectorGUI();

        MirrorObjectsTool tool = (MirrorObjectsTool)target;

        if (GUILayout.Button("Mirror Selected Objects"))
        {
            tool.MirrorSelectedObjects();
        }
    }
}
```

`Assets/Scripts/MirrorObjectsTool`

```c++
using UnityEngine;
using UnityEditor;

public class MirrorObjectsTool : MonoBehaviour
{
    public void MirrorSelectedObjects()
    {
        Transform[] selectedObjects = Selection.transforms;

        foreach (Transform originalObject in selectedObjects)
        {
            Vector3 mirrorPosition = originalObject.position;
            mirrorPosition.x = 2 * mirrorPosition.x;

            Vector3 mirrorRotation = originalObject.eulerAngles;
            mirrorRotation.y = -mirrorRotation.y;
            mirrorRotation.z = -mirrorRotation.z;

            GameObject mirroredObject = Instantiate(originalObject.gameObject, mirrorPosition, Quaternion.Euler(mirrorRotation));
            mirroredObject.transform.localScale = new Vector3(-mirroredObject.transform.localScale.x, mirroredObject.transform.localScale.y, mirroredObject.transform.localScale.z);

            Undo.RegisterCreatedObjectUndo(mirroredObject, "Mirror Objects");
        }
    }
}
```

