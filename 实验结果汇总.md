# 高性能计算实战结果汇总

## 1. NeRF 三维重建

完成 Lego 数据集的轻量 NeRF 训练与 `render_only` 测试。训练 20000 次后，最终 PSNR 为 10.08 dB，并保存 `020000.tar` 检查点、测试图像、视频和 Slurm 日志。当前轻量模型的测试图像接近纯白，结果用于验证离线环境、GPU 训练和渲染流程。

![NeRF 测试视角](NeRF/logs/blender_lego_light/renderonly_test_019999/000.png)

## 2. WRF 气象模拟

完成 WRF `em_quarter_ss` 算例运行，生成 `wrfout_d01_0001-01-01_00_00_00` 原始输出和最低模式层位温图。00:00 至 01:00 的图像显示局地低位温扰动逐渐扩展，并形成明显的低位温核心与周边波动结构。

![WRF 01:00 位温场](WRF/figures_theta_lowest/theta_lowest_002_0001-01-01_01-00-00.png)

## 3. PRESTO 并行性能测试

完成 `accelsearch` 和 `prepdata` 在 1、2、4、8、16 CPU 下的三次重复测试。`accelsearch` 在 16 CPU 时平均约 0.20 s，较 1 CPU 缩短约 14%；`prepdata` 在 4–8 CPU 时约 0.34 s，16 CPU 时因并行开销升至约 0.50 s。

![PRESTO 平均时间](PRESTO/微信图片_2026-08-27_101924_268.jpg)

## 文件目录

- `NeRF/`：模型检查点、训练与渲染结果、日志、原始结果包和单项说明。
- `WRF/`：WRF 原始输出、最低模式层位温图和单项说明。
- `PRESTO/`：三次运行图、平均时间图和单项说明。
