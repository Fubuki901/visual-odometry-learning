# Chapter 1 - Overview
视觉里程计和视觉算法，目标是了解如何使用视觉算法仅根据其图像估计相机的位置和运动，可以用于机器人、汽车和无人机，以实现自主运动。

使用其他传感器类型的方法包括车轮里程计、GPS和Inertial measurement units(IMU)。

对图像的要求：
* 特征目标静止
* 一定的光照条件
* 连续的图像帧


## 相关的视觉算法

下面罗列了一些视觉算法，可以解决不同方面的问题，注意理解这些算法的区别、各自的目标和它们之间的联系。

参考资料：

https://www.xjx100.cn/news/396111.html?action=onClick （SFM、VO和SLAM介绍）

### Structure from Motion (SFM)

传统三维重建，它更注重的是建图。估计的是相机姿态而非运动，输入不要求是连续的序列（OV要求连续序列），只要有不同角度的图像就可以重建。
一般用于后处理算法，很难用于有实时要求的应用。

### Visual SLAM (VSLAM)

SLAM要求解决是同步建图与定位问题，重点是定位。VO虽然能保证局部一致性，但有误差积累问题。SLAM允许后续做全局一致性检查（loop closure）。


![VO relations](./img/chapter_1/sfm_vslam_vo.png)

可看作包含关系。

VO流程大体相近。输入连续图像，然后检测图像中的特征点，并且再序列中匹配跟踪特征点，从特征点在图像中的位移来估计相机的移动，最后使用局部的优化方法优化估计结果。

基本workflow：

1. 读取连续输入图像
2. 提取特征
3. 做特征匹配和跟踪
4. 运动估计
5. 做局部优化

![feature detection](./img/chapter_1/input.png)

![feature detection](./img/chapter_1/feature_detection.png)

![feature matching](./img/chapter_1/feature_matching.png)

![feature matching](./img/chapter_1/motion_estimation.png)


