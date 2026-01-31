# PNDbotics Adam_lite描述(MJCF)

需要MuJoCo 2.3.3或更高版本。

## 概述

此包包含[由PNDbotics开发的Adam_lite人形机器人](https://www.pndbotics.com/humanoid)的简化机器人描述(MJCF)。

<p float="left">
  <img src="adam_lite.png" width="400">
</p>

## URDF → MJCF推导步骤

1. 使用[Maya](https://www.autodesk.com/sg/products/maya/overview?term=1-YEAR&tab=subscription)将DAE[网格文件](https://github.com/RethinkRobotics/sawyer_robot/tree/master/sawyer_description/meshes)转换为OBJ格式。
2. 使用[`obj2mjcf`](https://github.com/kevinzakka/obj2mjcf)处理`.obj`文件。
3. 在URDF的`<robot>`子句中添加`<mujoco> <compiler discardvisual="false"/> </mujoco>`以保留视觉几何体。
4. 将URDF加载到MuJoCo中并保存相应的MJCF。
5. 手动编辑MJCF以将公共属性提取到`<default>`部分。
6. 手动设计碰撞几何体。
7. 添加`scene.xml`，其中包含机器人、带有纹理的地面、天空盒和薄雾。

## 许可证

该模型根据[MIT许可证](LICENSE)发布。