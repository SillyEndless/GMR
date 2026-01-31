# GMR: 通用运动重定向

  <a href="https://arxiv.org/abs/2505.02833">
    <img src="https://img.shields.io/badge/paper-arXiv%3A2505.02833-b31b1b.svg" alt="arXiv 论文"/>
  </a> <a href="https://arxiv.org/abs/2510.02252">
    <img src="https://img.shields.io/badge/paper-arXiv%3A2510.02252-b31b1b.svg" alt="arXiv 论文"/>
  </a> <a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="许可证: MIT"/>
  </a> <a href="https://github.com/YanjieZe/GMR/releases">
    <img src="https://img.shields.io/badge/version-0.2.0-blue.svg" alt="版本"/>
  </a> <a href="https://x.com/ZeYanjie/status/1952446745696469334">
    <img src="https://img.shields.io/badge/twitter-ZeYanjie-blue.svg" alt="Twitter"/>
  </a> <a href="https://yanjieze.github.io/humanoid-foundation/#GMR">
    <img src="https://img.shields.io/badge/blog-GMR-blue.svg" alt="博客"/>
  </a> <a href="https://www.bilibili.com/video/BV1p1nazeEzC/?share_source=copy_web&vd_source=c76e3ab14ac3f7219a9006b96b4b0f76">
    <img src="https://img.shields.io/badge/tutorial-BILIBILI-blue.svg" alt="教程"/>
  </a>

![GMR横幅](./assets/GMR.png)

![GMR](./assets/GMR_pipeline.png)

#### GMR的关键特性:
- 实时高质量重定向，解锁实时全身遥操作的潜力，即[TWIST](https://github.com/YanjieZe/TWIST)。
- 为RL跟踪策略的良好性能精心调整。
- 支持多种人形机器人和多种人体运动数据格式(见下表)。

> [!注意]
> 如果您希望此仓库支持新机器人或新的人体运动数据格式，请将机器人文件(`.xml`, `.urdf`和网格) / 人体运动数据发送给<a href="mailto:lastyanjieze@gmail.com">Yanjie Ze</a>或创建一个issue，我们将尽快支持。请确保您发送的机器人文件可以在本仓库中开源。

本仓库采用[MIT许可证](LICENSE)授权。

# 新闻与更新
- **2026-01-21:** GMR现在支持[Xsens](https://www.xsens.com/) BVH离线数据。
- **2026-01-12:** GMR现在支持[Fourier GR3](https://www.fftai.com/)，这是仓库中的第17个人形机器人。
- **2025-12-02:** GMR现在支持[TWIST2](https://yanjieze.com/TWIST2)，它利用了[XRoboToolkit SDK](https://github.com/XR-Robotics/XRoboToolkit-PC-Service)。
- **2025-11-17:** 要加入我们的社区讨论，您可以添加我的微信联系[二维码](https://yanjieze.com/TWIST2/images/my_wechat.jpg)，信息如"[GMR] [您的姓名] [您的机构]"。
- **2025-11-08:** Jason Peng的[MimicKit]现在支持GMR格式。查看[这里](https://github.com/xbpeng/MimicKit/tree/main/tools/gmr_to_mimickit)。
- **2025-10-15:** 现在支持[PAL Robotics的Talos](https://pal-robotics.com/robot/talos/)，这是第15个人形机器人。
- **2025-10-14:** GMR现在支持[Nokov](https://www.nokov.com/) BVH数据。
- **2025-10-14:** 添加了关于ik配置的文档。参见[DOC.md](DOC.md)
- **2025-10-09:** 查看[TWIST](https://github.com/YanjieZe/TWIST)开源代码了解RL运动跟踪。
- **2025-10-02:** GMR的技术报告现在发布在[arXiv](https://arxiv.org/abs/2510.02252)上。
- **2025-10-01:** GMR现在支持将GMR pickle文件转换为CSV(用于beyondmimic)，查看`scripts/batch_gmr_pkl_to_csv.py`。
- **2025-09-25:** GMR的介绍可在[Bilibili](https://www.bilibili.com/video/BV1p1nazeEzC/?share_source=copy_web&vd_source=c76e3ab14ac3f7219a9006b96b4b0f76)上获得。
- **2025-09-16:** GMR现在支持使用[GVHMR](https://github.com/zju3dv/GVHMR)从**单目视频**中提取人体姿态并重定向到机器人。
- **2025-09-12:** GMR现在支持[Tienkung](https://github.com/Open-X-Humanoid/TienKung-Lab)，这是仓库中的第14个人形机器人。
- **2025-08-30:** GMR现在支持[Unitree H1 2](https://www.unitree.com/cn/h1)和[PND Adam Lite](https://pndbotics.com/)，分别是仓库中的第12和第13个人形机器人。
- **2025-08-28:** GMR现在支持[Booster T1](https://www.boosterobotics.com/)的23dof和29dof两种版本。
- **2025-08-28:** GMR现在支持使用从[OptiTrack](https://www.optitrack.com/)导出的离线FBX运动数据。
- **2025-08-27:** GMR现在支持[Berkeley Humanoid Lite](https://github.com/HybridRobotics/Berkeley-Humanoid-Lite-Assets)，这是仓库中的第11个人形机器人。
- **2025-08-24:** GMR现在支持[Unitree H1](https://www.unitree.com/h1/)，这是仓库中的第10个人形机器人。
- **2025-08-24:** GMR现在支持机器人的速度限制，`GeneralMotionRetargeting`类中默认`use_velocity_limit=True`(我们默认使用3*pi作为速度限制)；我们还默认添加了打印机器人DoF/Body/Motor名称及其ID的功能，您可以通过`robot_dof_names`、`robot_body_names`和`robot_motor_names`属性访问它们。
- **2025-08-10:** GMR现在支持[Booster K1](https://www.boosterobotics.com/)，这是仓库中的第9个机器人。
- **2025-08-09:** GMR现在支持*带Dex31手的Unitree G1*。
- **2025-08-07:** GMR现在支持[Galexea R1 Pro](https://galaxea-dynamics.com/)(这是一个轮式人形机器人！)和[KUAVO](https://www.kuavo.ai/)，分别是仓库中的第7和第8个人形机器人。
- **2025-08-06:** GMR现在支持[HighTorque Hi](https://www.hightorquerobotics.com/hi/)，这是仓库中的第6个人形机器人。
- **2025-08-04:** GMR初始发布。查看我们的[twitter帖子](https://x.com/ZeYanjie/status/1952446745696469334)。

## 演示

<table>
  <tr>
    <td align="center" width="20%">
      <b>演示 1</b><br>
      将LAFAN1舞蹈动作重定向到5个机器人。<br>
      <video src="https://github.com/user-attachments/assets/23566fa5-6335-46b9-957b-4b26aed11b9e" width="200" controls></video>
    </td>
    <td align="center" width="20%">
      <b>演示 2</b><br>
      Galexea R1 Pro机器人(视角1)。<br>
      <video src="https://github.com/user-attachments/assets/903ed0b0-0ac5-4226-8f82-5a88631e9b7c" width="200" controls></video>
    </td>
    <td align="center" width="20%">
      <b>演示 3</b><br>
      Galexea R1 Pro机器人(视角2)。<br>
      <video src="https://github.com/user-attachments/assets/deea0e64-f1c6-41bc-8661-351682006d5d" width="200" controls></video>
    </td>
    <td align="center" width="20%">
      <b>演示 4</b><br>
      通过更改一个参数切换机器人。<br>
      <video src="https://github.com/user-attachments/assets/03f10902-c541-40b1-8104-715a5759fd5e" width="200" controls></video>
    </td>
    <td align="center" width="20%">
      <b>演示 5</b><br>
      HighTorque机器人做扭舞。<br>
      <video src="https://github.com/user-attachments/assets/1d3e663b-f29e-41b1-8e15-5c0deb6a4a5c" width="200" controls></video>
    </td>
  </tr>

  <tr>
    <td align="center">
      <b>演示 6</b><br>
      Kuavo机器人拿起一个箱子。<br>
      <video src="https://github.com/user-attachments/assets/02fc8f41-c363-484b-a329-4f4e83ed5b80" width="200" controls></video>
    </td>
    <td align="center">
      <b>演示 7</b><br>
      Unitree H1机器人跳恰恰舞。<br>
      <video src="https://github.com/user-attachments/assets/28ee6f0f-be30-42bb-8543-cf1152d97724" width="200" controls></video>
    </td>
    <td align="center">
      <b>演示 8</b><br>
      Booster T1机器人跳跃(视角1)。<br>
      <video src="https://github.com/user-attachments/assets/2c75a146-e28f-4327-930f-5281bfc2ca9c" width="200" controls></video>
    </td>
    <td align="center">
      <b>演示 9</b><br>
      Booster T1机器人跳跃(视角2)。<br>
      <video src="https://github.com/user-attachments/assets/ff10c7ef-4357-4789-9219-23c6db8dba6d" width="200" controls></video>
    </td>
    <td align="center">
      <b>演示 10</b><br>
      Unitree H1-2机器人跳跃。<br>
      <video src="https://github.com/user-attachments/assets/2382d8ce-7902-432f-ab45-348a11eeb312" width="200" controls></video>
    </td>
  </tr>

  <tr>
    <td align="center">
      <b>演示 11</b><br>
      PND Adam Lite机器人。<br>
      <video src="https://github.com/user-attachments/assets/a8ef1409-88f1-4393-9cd0-d2b14216d2a4" width="200" controls></video>
    </td>
    <td align="center">
      <b>演示 12</b><br>
      Tienkung机器人行走。<br>
      <video src="https://github.com/user-attachments/assets/7a775ecc-4254-450c-a3eb-49e843b8e331" width="200" controls></video>
    </td>
    <td align="center">
      <b>演示 13</b><br>
      提取人体姿态(GVHMR + GMR)。<br>
      <a href="https://www.bilibili.com/video/BV1Tnpmz9EaE">▶ 在Bilibili观看</a>
    </td>
    <td align="center">
      <b>演示 14</b><br>
      PAL Robotics的Talos机器人格斗。<br>
      <video src="https://github.com/user-attachments/assets/3ec0bf80-80c1-4181-a623-dc2b072c2ca2" width="200" controls></video>
    </td>
    <td align="center">
      <b>演示 15</b><br>
      (如果您稍后添加新内容的可选占位符！)<br>
      <i>即将推出...</i>
    </td>
  </tr>
</table>

## 支持的机器人和数据格式

| 指定ID | 机器人/数据格式 | 机器人自由度 | SMPLX ([AMASS](https://amass.is.tue.mpg.de/), [OMOMO](https://github.com/lijiaman/omomo_release)) | BVH [LAFAN1](https://github.com/ubisoft/ubisoft-laforge-animation-dataset)| FBX ([OptiTrack](https://www.optitrack.com/)) |  BVH [Nokov](https://www.nokov.com/) | PICO ([XRoboToolkit](https://github.com/XR-Robotics/XRoboToolkit-PC-Service)) | 更多格式即将到来 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | Unitree G1 `unitree_g1` | 腿部 (2\*6) + 腰部 (3) + 手臂 (2\*7) = 29 | ✅ | ✅ | ✅ |  ✅ | ✅ |
| 1 | Unitree G1带手 `unitree_g1_with_hands` | 腿部 (2\*6) + 腰部 (3) + 手臂 (2\*7) + 手 (2\*7) = 43 | ✅ | ✅ | ✅ | 待定 | 待定 |
| 2 | Unitree H1 `unitree_h1` | 腿部 (2\*5) + 腰部 (1) + 手臂 (2\*4) = 19 | ✅ | 待定 | 待定 | 待定 | 待定 |
| 3 | Unitree H1 2 `unitree_h1_2` | 腿部 (2\*6) + 腰部 (1) + 手臂 (2\*7) = 27 | ✅ | 待定 | 待定 | 待定 | 待定 |
| 4 | Booster T1 `booster_t1` | 待定 | ✅ |  待定  | 待定 | 待定 |
| 5 | Booster T1 29dof `booster_t1_29dof` | 待定 | ✅ |  ✅  | 待定 | 待定 |
| 6 | Booster K1 `booster_k1` | 颈部 (2) + 手臂 (2\*4) + 腿部 (2\*6) = 22 | ✅ | 待定 | 待定 | 待定 |
| 7 | 斯坦福ToddlerBot `stanford_toddy` | 待定 | ✅ | ✅ | 待定 | 待定 |
| 8 | Fourier N1 `fourier_n1` | 待定 | ✅ | ✅ | 待定 | 待定 |
| 9 | ENGINEAI PM01 `engineai_pm01` | 待定 | ✅ | ✅ | 待定 | 待定 |
| 10 | HighTorque Hi `hightorque_hi` | 头部 (2) + 手臂 (2\*5) + 腰部 (1) + 腿部 (2\*6) = 25 | ✅ | 待定 | 待定 | 待定 |
| 11 | Galaxea R1 Pro `galaxea_r1pro` (这是一个轮式机器人！) | 底座 (6) + 躯干 (4) + 手臂 (2*7) = 24 | ✅ | 待定 | 待定 | 待定 |
| 12 | Kuavo `kuavo_s45` |  头部 (2) + 手臂 (2\*7) + 腿部 (2\*6) = 28 | ✅ | 待定 | 待定 | 待定 |
| 13 | Berkeley Humanoid Lite `berkeley_humanoid_lite` (需要进一步调整) | 腿部 (2\*6) + 手臂 (2\*5) = 22 | ✅ | 待定 | 待定 | 待定 |
| 14 | PND Adam Lite `pnd_adam_lite`  | 腿部 (2\*6) + 腰部 (3) + 手臂 (2\*5) = 25 | ✅ | 待定 | 待定 | 待定 |
| 15 | Tienkung `tienkung`  | 腿部 (2\*6) + 手臂 (2\*4) = 20 | ✅ | 待定 | 待定 | 待定 |
| 16 | PAL Robotics的Talos `pal_talos`  | 头部 (2) + 手臂 (2\*7) + 腰部 (2) + 腿部 (2\*6) = 30 | ✅ | 待定 | 待定 | 待定 |
| 17 | Fourier GR3 `fourier_gr3`  | 头部 (2) + 手臂 (2\*7) + 腰部 (3) + 腿部 (2\*6) = 31 | ✅ | 待定 | 待定 | 待定 |
| 更多机器人即将到来！ |
| 18 | AgiBot A2 `agibot_a2` | 待定 | 待定 | 待定 | 待定 | 待定 |
| 19 | OpenLoong `openloong` | 待定 | 待定 | 待定 | 待定 | 待定 |

## 安装

> [!注意]
> 代码已在Ubuntu 22.04/20.04上测试。

首先创建您的conda环境：

```bash
conda create -n gmr python=3.10 -y
conda activate gmr
```

然后，安装GMR：

```bash
pip install -e .
```

安装SMPLX后，如果您使用的是SMPL-X pkl文件，请将`smplx/body_models.py`中的`ext`从`npz`更改为`pkl`。

为了解决一些可能的渲染问题：

```bash
conda install -c conda-forge libstdcxx-ng -y
```

## 数据准备

[[SMPLX](https://github.com/vchoutas/smplx) 身体模型] 从[SMPL-X](https://smpl-x.is.tue.mpg.de/)下载SMPL-X身体模型到`assets/body_models`，然后按以下方式组织：
```bash
- assets/body_models/smplx/
-- SMPLX_NEUTRAL.pkl
-- SMPLX_FEMALE.pkl
-- SMPLX_MALE.pkl
```

[[AMASS](https://amass.is.tue.mpg.de/) 运动数据] 从[AMASS](https://amass.is.tue.mpg.de/)下载原始SMPL-X数据到任意您想要的文件夹。注意：不要下载SMPL+H数据。

[[OMOMO](https://github.com/lijiaman/omomo_release) 运动数据] 从[this google drive文件](https://drive.google.com/file/d/1tZVqLB7II0whI-Qjz-z-AU3ponSEyAmm/view?usp=sharing)下载原始OMOMO数据到任意您想要的文件夹。并使用`scripts/convert_omomo_to_smplx.py`将数据处理成SMPL-X格式。

[[LAFAN1](https://github.com/ubisoft/ubisoft-laforge-animation-dataset) 运动数据] 从[官方仓库](https://github.com/ubisoft/ubisoft-laforge-animation-dataset)下载原始LAFAN1 bvh文件，即[lafan1.zip](https://github.com/ubisoft/ubisoft-laforge-animation-dataset/blob/master/lafan1/lafan1.zip)。

## 人体/机器人运动数据公式化

为了更好地使用这个库，您可以先了解我们使用的人体运动数据和我们获得的机器人运动数据。

每一帧的**人体运动数据**被表述为(human_body_name, 3d全局平移 + 全局旋转)的字典。旋转通常表示为四元数(默认为wxyz顺序，以与mujoco对齐)。

每一帧的**机器人运动数据**可以理解为(robot_base_translation, robot_base_rotation, robot_joint_positions)的元组。

## 使用方法

### [新增] PICO流式传输到机器人(TWIST2)

安装PICO SDK:
1. 在您的PICO上，安装PICO SDK: 参见[这里](https://github.com/XR-Robotics/XRoboToolkit-Unity-Client/releases/)。
2. 在您自己的PC上，
    - 下载[ubuntu 22.04的deb包](https://github.com/XR-Robotics/XRoboToolkit-PC-Service/releases/download/v1.0.0/XRoboToolkit_PC_Service_1.0.0_ubuntu_22.04_amd64.deb)，或从[仓库源码](https://github.com/XR-Robotics/XRoboToolkit-PC-Service)构建。
    - 要安装，请使用命令
        ```bash
        sudo dpkg -i XRoboToolkit_PC_Service_1.0.0_ubuntu_22.04_amd64.deb
        ```
        然后您应该在APPs中看到`xrobotoolkit-pc-service`。记得在进行遥操作之前启动此应用程序。
    - 构建PICO PC Service SDK和用于PICO流式的Python SDK：
        ```bash
        conda activate gmr

        git clone https://github.com/YanjieZe/XRoboToolkit-PC-Service-Pybind.git
        cd XRoboToolkit-PC-Service-Pybind

        mkdir -p tmp
        cd tmp
        git clone https://github.com/XR-Robotics/XRoboToolkit-PC-Service.git
        cd XRoboToolkit-PC-Service/RoboticsService/PXREARobotSDK
        bash build.sh
        cd ../../../..


        mkdir -p lib
        mkdir -p include
        cp tmp/XRoboToolkit-PC-Service/RoboticsService/PXREARobotSDK/PXREARobotSDK.h include/
        cp -r tmp/XRoboToolkit-PC-Service/RoboticsService/PXREARobotSDK/nlohmann include/nlohmann/
        cp tmp/XRoboToolkit-PC-Service/RoboticsService/PXREARobotSDK/build/libPXREARobotSDK.so lib/
        # rm -rf tmp

        # 构建项目
        conda install -c conda-forge pybind11
        pip uninstall -y xrobotoolkit_sdk
        python setup.py install
        ```

您应该全部设置好了！

要尝试它，请查看[TWIST2的这个脚本](https://github.com/amazon-far/TWIST2/blob/master/teleop.sh)：
```bash
bash teleop.sh
```
您应该能够在mujoco窗口中看到重定向的机器人运动。

### 从SMPL-X(AMASS, OMOMO)到机器人的重定向

> [!注意]
> 注意：安装SMPL-X后，如果您使用的是SMPL-X pkl文件，请将`smplx/body_models.py`中的`ext`从`npz`更改为`pkl`。

重定向单个运动：

```bash
python scripts/smplx_to_robot.py --smplx_file <smplx数据路径> --robot <机器人数据路径> --save_path <保存机器人数据.pkl的路径> --rate_limit
```

默认情况下，您应该能在mujoco窗口中看到重定向机器人运动的可视化。
如果要录制视频，请添加`--record_video`和`--video_path <您的视频路径,mp4>`。

- `--rate_limit`用于限制重定向机器人运动的速率以保持与人体运动相同。如果您希望尽可能快，请删除`--rate_limit`。

重定向一个文件夹的运动：

```bash
python scripts/smplx_to_robot_dataset.py --src_folder <smplx数据目录路径> --tgt_folder <保存机器人数据的目录路径> --robot <机器人名称>
```

默认情况下，批量重定向没有可视化。

### 从GVHMR到机器人的重定向

首先，按照[他们的官方说明](https://github.com/zju3dv/GVHMR/blob/main/docs/INSTALL.md)安装GVHMR。

然后运行他们的演示，可以从单目视频中提取人体姿态：

```bash
cd path/to/GVHMR
python tools/demo/demo.py --video=docs/example_video/tennis.mp4 -s
```

然后您应该在`GVHMR/outputs/demo/tennis/hmr4d_results.pt`中获得保存的人体姿态数据。

然后，运行下面的命令将提取的人体姿态数据重定向到您的机器人：

```bash
python scripts/gvhmr_to_robot.py --gvhmr_pred_file <hmr4d_results.pt路径> --robot unitree_g1 --record_video
```

## 从BVH(LAFAN1, Nokov)到机器人的重定向

重定向单个运动：

```bash
# 单个运动
python scripts/bvh_to_robot.py --bvh_file <bvh数据路径> --robot <机器人数据路径> --save_path <保存机器人数据.pkl的路径> --rate_limit --format <格式>
```

默认情况下，您应该能在mujoco窗口中看到重定向机器人运动的可视化。
- `--rate_limit`用于限制重定向机器人运动的速率以保持与人体运动相同。如果您希望尽可能快，请删除`--rate_limit`。
- `--format`用于指定BVH数据的格式。支持的格式为`lafan1`和`nokov`。

重定向一个文件夹的运动：

```bash
python scripts/bvh_to_robot_dataset.py --src_folder <bvh数据目录路径> --tgt_folder <保存机器人数据的目录路径> --robot <机器人名称>
```

默认情况下，批量重定向没有可视化。

## 从BVH(Xsens)到机器人的重定向

#### 使用mujoco可视化bvh数据：

安装PyQt6:
```bash
pip install PyQt6 PyQt6-Qt6 PyQt6-sip
```

```bash
python general_motion_retargeting/utils/xsens_vendor/mujoco_xsens_bvh_view.py \
  --bvh_file <bvh数据目录路径> \
  --scale <位移缩放大小> \
  --reset_to_zero
```
例如
```bash
python general_motion_retargeting/utils/xsens_vendor/mujoco_xsens_bvh_view.py \
  --scale 0.01 \
  --bvh_file assets/xsens_bvh_test/251021_04_boxing_120Hz_cm_3DsMax.bvh \
  --reset_to_zero
```

- `--start`用于指定初始处理帧。如果没有输入，默认从第一帧开始处理。
- `--end`用于指定最终处理帧。如果没有输入，默认处理到最后一个帧。
- `--reset_to_zero`用于将位移和Z轴旋转重置为零。此功能与`--start`结合使用时，可以很好地将数据设置为初始零位置。因为有时某些数据集的前一两帧与后续数据差异太大，这些数据需要丢弃。
- `--scale`用于设置位移的缩放值，这取决于数据集中位移所使用的单位与米的关系。
- ##### 使用前必须安装PyQt6。`pip install PyQt6`
- ##### 执行此命令后，将启动一个UI界面，使您能够调整每个关节在x、y和z方向上的每个通道的角度值。完成调整后，点击"应用和预览"按钮，将在本地生成一个`offset.json`文件并对BVH文件执行MuJoCo可视化播放。当运行`xsens_bvh_to_robot.py`时，它将读取此JSON文件中的数据。因此，在使用`xsens_bvh_to_robot.py`进行运动重定向之前，您需要先执行`mujoco_xsens_bvh_view.py`，以确保`offset.json`文件在本地存在。

#### 重定向单个运动：
```bash
# 单个运动
python scripts/xsens_bvh_to_robot.py \
  --bvh_file <bvh数据路径> \
  --robot <机器人数据路径> \
  --save_path <保存机器人数据.pkl的路径> \
  --rate_limit \
  --start <第一帧的编号> \
  --scale <位移缩放大小> \
  --reset_to_zero \
  --bvh_format <导出的bvh格式>
```
例如
```bash
python scripts/xsens_bvh_to_robot.py  \
  --robot unitree_h1_2 \
  --scale 0.01 \
  --reset_to_zero \
  --bvh_format 3DSM \
  --bvh_file assets/xsens_bvh_test/251021_04_boxing_120Hz_cm_3DsMax.bvh \
  --save_path retargeting_data/h1/251021_04_boxing_120Hz_cm_3DsMax.pkl
```
##### 默认情况下，您应该能在mujoco窗口中看到重定向机器人运动的可视化。
- `--rate_limit`用于限制重定向机器人运动的速率以保持与人体运动相同。如果您希望尽可能快，请删除`--rate_limit`。
- `--start`用于指定初始处理帧。如果没有输入，默认从第一帧开始处理。
- `--end`用于指定最终处理帧。如果没有输入，默认处理到最后一个帧。
- `--reset_to_zero`用于将位移和Z轴旋转重置为零。此功能与`--start`结合使用时，可以很好地将数据设置为初始零位置。因为有时某些数据集的前一两帧与后续数据差异太大，这些数据需要丢弃。
- `--scale`用于设置位移的缩放值，这取决于数据集中位移所使用的单位与米的关系。
##### ！！！！！！！！！！！！！！！！！！ 注意 ！！！！！！！！！！！！！！！！！！！！
- `--bvh_format`用于设置要解析的bvh格式。在Xsens MVN软件中，可以导出三种格式的BVH文件。不同格式的BVH文件会有一些差异。这里我推荐使用3D Studio Max格式。(实际上，我还没有完成其他格式数据的解析。)
- 导出的pkl文件将以`wxyz`格式表示四元数。^ _ ^

### 从FBX(OptiTrack)到机器人的重定向

#### 离线FBX文件

重定向单个运动：

1. 按照[这些说明](https://github.com/nv-tlabs/ASE/tree/main/ase/poselib#importing-from-fbx)和[这些说明](https://github.com/nv-tlabs/ASE/issues/61#issuecomment-2670315114)安装`fbx_sdk`。您可能需要为此创建一个新的conda环境。
2. 激活您安装了`fbx_sdk`的conda环境。
使用以下命令从您的`.fbx`文件中提取运动数据：

```bash
cd third_party
python poselib/fbx_importer.py --input <fbx文件路径.fbx> --output <保存运动数据.pkl的路径> --root-joint <根关节名称> --fps <fps>
```

3. 然后，运行下面的命令将提取的运动数据重定向到您的机器人：

```bash
conda activate gmr
# 单个运动
python scripts/fbx_offline_to_robot.py --motion_file <保存的运动数据.pkl路径> --robot <机器人数据路径> --save_path <保存机器人数据.pkl的路径> --rate_limit
```

默认情况下，您应该能在mujoco窗口中看到重定向机器人运动的可视化。

- `--rate_limit`用于限制重定向机器人运动的速率以保持与人体运动相同。如果您希望尽可能快，请删除`--rate_limit`。

#### 在线流式传输

我们提供了使用OptiTrack MoCap数据进行实时流式传输和重定向的脚本。

通常您会有两台计算机，一台是安装了Motive(用于OptiTrack的桌面APP)的服务器，另一台是安装了GMR的客户端。

找到服务器IP(安装了Motive的计算机)和客户端IP(您的计算机)。按如下方式设置流式传输：

![OptiTrack 流式传输](./assets/optitrack.png)

然后运行：

```bash
python scripts/optitrack_to_robot.py --server_ip <服务器IP> --client_ip <客户端IP> --use_multicast False --robot unitree_g1
```

您应该能在mujoco窗口中看到重定向机器人运动的可视化。

### 可视化保存的机器人运动

可视化单个运动：

```bash
python scripts/vis_robot_motion.py --robot <机器人名称> --robot_motion_path <保存机器人数据的路径.pkl>
```

如果要录制视频，请添加`--record_video`和`--video_path <您的视频路径,mp4>`。

可视化一个文件夹的运动：

```bash
python scripts/vis_robot_motion_dataset.py --robot <机器人名称> --robot_motion_folder <保存机器人数据文件夹的路径>
```

启动MuJoCo可视化窗口并点击它后，您可以使用以下键盘控制：
* `[`: 播放上一个运动
* `]`: 播放下一个运动
* `空格键`: 切换播放/暂停

## 速度基准测试

| CPU | 重定向速度 |
| --- | --- |
| AMD Ryzen Threadripper 7960X 24核 | 60~70 FPS |
| 13代Intel Core i9-13900K 24核 | 35~45 FPS |
| 待定 | 待定 |

## 引用

如果您觉得我们的代码有用，请考虑引用我们的相关论文：

```bibtex
@article{joao2025gmr,
  title={Retargeting Matters: General Motion Retargeting for Humanoid Motion Tracking},
  author= {Joao Pedro Araujo and Yanjie Ze and Pei Xu and Jiajun Wu and C. Karen Liu},
  year= {2025},
  journal= {arXiv preprint arXiv:2510.02252}
}
```

```bibtex
@article{ze2025twist,
  title={TWIST: Teleoperated Whole-Body Imitation System},
  author= {Yanjie Ze and Zixuan Chen and João Pedro Araújo and Zi-ang Cao and Xue Bin Peng and Jiajun Wu and C. Karen Liu},
  year= {2025},
  journal= {arXiv preprint arXiv:2505.02833}
}
```

以及这个github仓库：

```bibtex
@software{ze2025gmr,
  title={GMR: General Motion Retargeting},
  author= {Yanjie Ze and João Pedro Araújo and Jiajun Wu and C. Karen Liu},
  year= {2025},
  url= {https://github.com/YanjieZe/GMR},
  note= {GitHub repository}
}
```

## 已知问题

为所有不同的人类设计单一配置并非易事。我们观察到某些运动可能有不良的重定向结果。如果您观察到一些不良结果，请告诉我们！我们现在在[TEST_MOTIONS.md](TEST_MOTIONS.md)中收集了此类运动。

## 致谢

我们的IK求解器基于[mink](https://github.com/kevinzakka/mink)和[mujoco](https://github.com/google-deepmind/mujoco)构建。我们的可视化基于[mujoco](https://github.com/google-deepmind/mujoco)构建。我们尝试的人体运动数据包括[AMASS](https://amass.is.tue.mpg.de/)、[OMOMO](https://github.com/lijiaman/omomo_release)和[LAFAN1](https://github.com/ubisoft/ubisoft-laforge-animation-dataset)。

原始机器人模型可以在以下位置找到：

* [Berkley Humanoid Lite](https://github.com/HybridRobotics/Berkeley-Humanoid-Lite-Assets): CC-BY-SA-4.0许可证
* [Booster K1](https://www.boosterobotics.com/)
* [Booster T1](https://booster.feishu.cn/wiki/UvowwBes1iNvvUkoeeVc3p5wnUg) ([英语](https://booster.feishu.cn/wiki/DtFgwVXYxiBT8BksUPjcOwG4n4f))
* [EngineAI PM01](https://github.com/engineai-robotics/engineai_ros2_workspace): [链接到文件](https://github.com/engineai-robotics/engineai_ros2_workspace/blob/community/src/simulation/mujoco/assets/resource)
* [Fourier N1](https://github.com/FFTAI/Wiki-GRx-Gym): [链接到文件](https://github.com/FFTAI/Wiki-GRx-Gym/tree/FourierN1/legged_gym/resources/robots/N1)
* [Galaxea R1 Pro](https://galaxea-dynamics.com/): MIT许可证
* [HighToqure Hi](https://www.hightorquerobotics.com/hi/)
* [LEJU Kuavo S45](https://gitee.com/leju-robot/kuavo-ros-opensource/blob/master/LICENSE): MIT许可证
* [PAL Robotics' Talos](https://github.com/google-deepmind/mujoco_menagerie): [链接到文件](https://github.com/google-deepmind/mujoco_menagerie/tree/main/pal_talos)
* [Toddlerbot](https://github.com/hshi74/toddlerbot): [链接到文件](https://github.com/hshi74/toddlerbot/tree/main/toddlerbot/descriptions/toddlerbot_active)
* [Unitree G1](https://github.com/unitreerobotics/unitree_ros): [链接到文件](https://github.com/unitreerobotics/unitree_ros/tree/master/robots/g1_description)