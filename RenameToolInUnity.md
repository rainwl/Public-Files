```c++
#if UNITY_EDITOR
using System.IO;
using UnityEditor;
using UnityEngine;

namespace CustomEditorWindow
{
    public class RenameTool : EditorWindow
    {
        #region members

        private Vector2 _scrollPos;
        private int _charSize;
        private string _targetName = string.Empty;
        private string _startNumStr = "0";
        private int _startNumINT = 0;

        #endregion

        #region get window

        [MenuItem("CustomEditorWindow/Rename Tool")]
        private static void OpenWindow()
        {
            GetWindow<RenameTool>("Rename Tool").Show();
        }

        #endregion

        #region render the window

        private void OnGUI()
        {
            _scrollPos = GUILayout.BeginScrollView(_scrollPos);
            {
                #region tool title

                _charSize = GUI.skin.label.fontSize;
                GUI.color = Color.yellow;
                GUILayout.Space(10);
                GUI.skin.label.fontSize = 24;
                GUI.skin.label.alignment = TextAnchor.MiddleCenter;
                GUILayout.Label("Rename Tool v1.0.0");
                GUI.skin.label.fontSize = _charSize;
                GUI.skin.label.alignment = TextAnchor.MiddleLeft;
                GUI.color = Color.white;
                GUILayout.Space(20);

                #endregion

                GUILayout.BeginVertical();
                {
                    #region text input

                    GUILayout.BeginHorizontal();
                    {
                        GUILayout.Label("Name Style: ");
                        GUILayout.FlexibleSpace();
                        _targetName = GUILayout.TextField(_targetName, GUILayout.Width(140));
                    }
                    GUILayout.EndHorizontal();
                    GUILayout.Space(10);

                    GUILayout.BeginHorizontal();
                    {
                        GUILayout.Label("Start Number: ");
                        GUILayout.FlexibleSpace();
                        _startNumStr = GUILayout.TextField(_startNumStr, GUILayout.Width(60));
                        _startNumINT = int.Parse(_startNumStr);
                    }
                    GUILayout.EndHorizontal();

                    #endregion

                    #region button

                    GUILayout.Space(30);
                    bool hasObject = (Selection.objects.Length > 0);
                    GUI.enabled = hasObject;

                    GUILayout.FlexibleSpace();
                    if (!hasObject)
                    {
                        GUI.color = Color.red;
                        GUILayout.Button("No Selected Objects!");
                        GUI.color = Color.white;
                    }
                    else
                    {
                        if (GUILayout.Button("Rename"))
                        {
                            Rename(_targetName, _startNumINT);
                        }
                    }

                    GUILayout.Space(20);

                    #endregion
                }
                GUILayout.EndVertical();
            }
            GUILayout.EndScrollView();
        }

        #endregion

        #region Rename Function

        private static void Rename(string tName, int tIndex)
        {
            var name = tName.Trim(); //去除头尾空白字符串
            var index = tIndex;
            if ((name + index) == string.Empty) return; //若名字不为空
            var isAssetsObject = false; //flag, 是否是assets文件夹的资源

            foreach (var o in Selection.objects)
            {
                var pathG = AssetDatabase.GetAssetPath(o); //获得选中物的路径
                //查看路径后缀
                if (Path.GetExtension(pathG) != "") //若后缀不为空, 则为assets文件夹物体
                {
                    if (name.Length >= 2 && name.Substring(0, 2) == "m_") // m_ 开头会被吞
                    {
                        //用 M_ 修正
                        var tempName = name.Remove(0, 1);
                        name = tempName.Insert(0, "M");
                    }

                    AssetDatabase.RenameAsset(pathG, name + index); //改名API
                    if (!isAssetsObject)
                    {
                        isAssetsObject = true; //修改flag
                    }
                }
                else //后缀为空, 是场景物体
                {
                    o.name = name + index;
                }

                index++;
            }

            if (!isAssetsObject) return; //若是assets文件夹资源, 则刷新assets
            AssetDatabase.SaveAssets();
            AssetDatabase.Refresh();
        }

        #endregion
    }
}
#endif
```