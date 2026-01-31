# CLAUDE.md

本文档为 Claude Code (claude.ai/code) 在处理此代码库时提供指导。

## 安装和设置

这是一个用于人形机器人运动重定向的Python包。以开发模式安装：

```bash
conda create -n gmr python=3.10 -y
conda activate gmr
pip install -e .
conda install -c conda-forge libstdcxx-ng -y
```

## 代码架构

### 核心组件

- **`GeneralMotionRetargeting`** (`general_motion_retargeting/motion_retarget.py`): 使用基于mink/mujoco构建的逆运动学(IK)求解器进行运动重定向的主要类
- **`KinematicsModel`** (`general_motion_retargeting/kinematics_model.py`): 处理机器人运动学计算
- **`RobotMotionViewer`** (`general_motion_retargeting/robot_motion_viewer.py`): 基于MuJoCo的机器人运动可视化
- **配置系统** (`general_motion_retargeting/params.py`): 简化的机器人定义和IK配置映射 - 精简以专注于核心支持的机器人

### 数据流

1. **人体运动输入**: SMPL-X (AMASS/OMOMO) 或 BVH (LAFAN1) 格式
2. **运动格式**: 每帧 = (human_body_name, 3D平移 + 旋转) 的字典
3. **机器人输出**: (base_translation, base_rotation, joint_positions) 的元组
4. **IK配置**: `general_motion_retargeting/ik_configs/` 中的JSON文件定义人体到机器人的身体映射

### 支持的机器人

`assets/` 目录中的核心机器人模型：
- Unitree G1 (`unitree_g1`) - 29自由度人形机器人
- Booster T1 (`booster_t1`) - 全身人形机器人
- Booster K1 (`booster_k1`) - 22自由度人形机器人
- 斯坦福ToddlerBot (`stanford_toddy`) - 研究用人形机器人
- Fourier N1 (`fourier_n1`) - 商用人形机器人
- ENGINEAI PM01 (`engineai_pm01`) - 工业人形机器人
- Kuavo S45 (`kuavo_s45`) - 28自由度人形机器人
- HighTorque Hi (`hightorque_hi`) - 25自由度人形机器人
- Galaxea R1 Pro (`galaxea_r1pro`) - 24自由度轮式人形机器人

ROBOT_BASE_DICT中保留的兼容模型：
- `unitree_g1_with_hands` (43自由度带灵巧手)
- `dex31_left_hand`, `dex31_right_hand` (手部组件)

## 常用命令

### 单次运动重定向
```bash
# SMPL-X 到机器人
python scripts/smplx_to_robot.py --smplx_file <路径> --robot <机器人名称> --save_path <输出.pkl>

# BVH 到机器人
python scripts/bvh_to_robot.py --bvh_file <路径> --robot <机器人名称> --save_path <输出.pkl>
```

### 批量处理
```bash
# 处理数据集
python scripts/smplx_to_robot_dataset.py
python scripts/bvh_to_robot_dataset.py
```

### 可视化
```bash
# 可视化保存的机器人运动
python scripts/vis_robot_motion.py --robot <机器人名称> --robot_motion_path <路径.pkl>
```

在任何可视化命令后添加 `--record_video --video_path <输出.mp4>` 来录制视频。

## 关键技术细节

- **IK求解器**: 使用mink库，可配置求解器(默认："daqp")和阻尼(默认：5e-1)
- **人体高度缩放**: 基于 `actual_human_height` 参数与配置假设的自动缩放
- **实时性能**: 针对高端CPU进行了遥操作用例的60-70 FPS优化
- **身体模型依赖**: 需要 `assets/body_models/smplx/` 中的SMPL-X身体模型

## 文件组织

- `scripts/`: 不同重定向工作流程的入口脚本
- `general_motion_retargeting/`: 核心库代码
- `assets/`: 机器人模型(MuJoCo XML)和身体模型(SMPL-X)
- `general_motion_retargeting/ik_configs/`: 人体到机器人身体映射的JSON配置文件：
  - SMPL-X配置: `smplx_to_{g1,t1,k1,toddy,n1,pm01,kuavo,hi,r1pro}.json`
  - BVH配置: `bvh_to_{g1,t1,toddy,n1,pm01}.json`
  - FBX配置: `fbx_to_g1.json`

## 项目状态与特性

**当前状态**: 具有广泛机器人支持的生产就绪运动重定向系统

**关键能力**:
- **多格式输入**: SMPL-X (AMASS/OMOMO), BVH (LAFAN1), FBX (OptiTrack)
- **实时性能**: 高端硬件上用于遥操作的60-70 FPS
- **9种机器人模型**: 从研究平台到商业人形机器人
- **鲁棒IK**: 基于mink的求解器，具有自动人体高度缩放
- **可视化**: 具有视频录制功能的MuJoCo查看器
- **批量处理**: 数据集级别的重定向工作流程

**使用案例**:
- 实时全身遥操作 (参见 [TWIST](https://github.com/YanjieZe/TWIST))
- RL策略训练数据生成
- 动作捕捉到机器人的部署
- 跨平台人形机器人运动传输

**近期新增** (2025):
- Booster K1支持 (第9个机器人)
- 灵巧手集成 (G1 + Dex31)
- 轮式人形机器人支持 (Galaxea R1 Pro)
- 增强的OptiTrack实时流