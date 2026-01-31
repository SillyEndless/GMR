# Unitree H1_2描述(URDF & MJCF)

## 概述

此包包括[Unitree H1_2](https://www.unitree.com/h1)的通用人形机器人描述(URDF & MJCF)，由[Unitree Robotics](https://www.unitree.com/)开发。

<p align="center">
  <img src="h1_2.png" width="500"/>
</p>

## 使用[MuJoCo](https://github.com/google-deepmind/mujoco)可视化

1. 打开MuJoCo查看器

   ```bash
   pip install mujoco
   python -m mujoco.viewer
   ```

2. 将MJCF模型文件(`h1_2.xml`或`h1_2_handless.xml`)拖放到MuJoCo查看器中。