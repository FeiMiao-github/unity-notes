Unity Graphical User Interface

# Unity 界面发展史

NGUI -> UGUI

* 全新的布局系统
* 强大的事件机制
* 最佳的执行效能
* UGUI没有Tween组件(常用iTween,DoTween)
* 开发效率略低于NGUI

## Canvas Render mode

* Screen Space - Overlay

  屏幕坐标系和世界坐标系原点重合

* Screen Space - Camera

  需要提供一个render Camera，Canvas对象被绘制在一个与摄像机固定距离的平面上，且绘制效果受到摄像机参数影响

  用于3D和2D同时显示在界面中

* World Space

  Canvas贴到3D物体表面