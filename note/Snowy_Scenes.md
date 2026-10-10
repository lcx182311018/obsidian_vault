

[ 原论文](Snowy_Scenes_A_Multimodal_Multitask_Dataset_Toward_Snow-Tonomous_Vehicles.pdf)
面向雪天自动驾驶的真实世界多模态、多任务数据集。作者用 128 线 LiDAR、RGB、三个热成像相机和 GNSS/IMU 采集了 2.2 万多帧数据，并对其中 5027 个 LiDAR scan 做了 3D bounding box、逐点语义以及雪花点标注。因此这个数据集可以同时 benchmark 3D semantic segmentation、LiDAR desnowing 和 3D object detection，并进一步研究 multitask learning。实验发现，在高分辨率雪天 LiDAR 上，voxel-based 方法在 segmentation 和 denoising 上最好，BEV-based 方法在 detection 上更好，而 point-based 方法整体较弱；同时 LiDAR-camera fusion 能显著提升检测性能。论文的核心价值不是提出一个新模型，而是提供了一个比较完整的真实雪天 3D perception benchmark。