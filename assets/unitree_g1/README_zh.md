# Unitree G1描述(URDF & MJCF)

## 概述

此包包括[Unitree G1](https://www.unitree.com/g1/)的通用人形机器人描述(URDF & MJCF)，由[Unitree Robotics](https://www.unitree.com/)开发。

G1机器人的MJCF/URDF文件：

| MJCF/URDF文件名           | `mode_machine` | 髋关节滚转减速比 | 更新状态 | 腿部自由度 | 腰部自由度 | 手臂自由度 | 手部自由度 |
| ----------------------------- | :------------: | :----------------------: | ------------- | :-----: | :-------: | :-----: | :------: |
| `g1_23dof`                    |       1        |           14.5           | Beta          |   6*2   |     1     |   5*2   |    0     |
| `g1_29dof`                    |       2        |           14.5           | Beta          |   6*2   |     3     |   7*2   |    0     |
| `g1_29dof_with_hand`          |       2        |           14.5           | Beta          |   6*2   |     3     |   7*2   |   7*2    |
| `g1_29dof_lock_waist`         |       3        |           14.5           | Beta          |   6*2   |     1     |   7*2   |    0     |
| `g1_23dof_rev_1_0`            |       4        |           22.5           | 最新          |   6*2   |     1     |   5*2   |    0     |
| `g1_29dof_rev_1_0`            |       5        |           22.5           | 最新          |   6*2   |     3     |   7*2   |    0     |
| `g1_29dof_with_hand_rev_1_0`  |       5        |           22.5           | 最新          |   6*2   |     3     |   7*2   |   7*2    |
| `g1_29dof_lock_waist_rev_1_0` |       6        |           22.5           | 最新          |   6*2   |     1     |   7*2   |    0     |
| `g1_dual_arm`                 |       9        |           null           | 最新          |    0    |     0     |   7*2   |    0     |

## 使用[MuJoCo](https://github.com/google-deepmind/mujoco)可视化

1. 打开MuJoCo查看器

   ```bash
   pip install mujoco
   python -m mujoco.viewer
   ```

2. 将MJCF/URDF模型文件(`g1_XXX.xml`/`g1_XXX.urdf`)拖放到MuJoCo查看器中。