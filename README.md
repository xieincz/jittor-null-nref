# Jittor 可微渲染新视角生成赛题
![主要结果](https://s3.bmp.ovh/imgs/2022/06/30/4c97c8a0b9092e7e.png)

![主要结果](https://s3.bmp.ovh/imgs/2022/06/30/9af1ea191571c8bf.png)

![主要结果](https://s3.bmp.ovh/imgs/2022/06/30/4446ba393a07f440.png)

![主要结果](https://s3.bmp.ovh/imgs/2022/06/30/811e962c4d69f45c.png)

![主要结果](https://s3.bmp.ovh/imgs/2022/06/30/927e5e29bece7c93.png)

## 简介
本项目包含了第二届计图挑战赛计图 - 可微渲染新视角生成赛题的代码实现。本项目的特点是：采用了 NeRF基于大量相机参数已知的图片训练神经网络，可以从任意角度渲染出图片结果。

## 安装 
在1张P100上训练1个50000次迭代的模型并且生成评分图像的时间约为4小时

#### 运行环境
- ubuntu 20.04 LTS
- python >= 3.7
- jittor >= 1.3.0

## 训练
单卡训练可运行以下命令：
```
python demo7-nerf.py --expname=Scar \
--basedir=./ \
--datadir=./nerf_synthetic/Scar \
--dataset_type=blender \
--no_batching \
--use_viewdirs \
--white_bkgd \
--lrate_decay=500 \
--N_samples=64 \
--N_importance=128 \
--N_rand=1024 \
--precrop_iters=500 \
--precrop_frac=0.5 \
--testskip=1 \
--N_iters=180001 \
--i_img=180000 \
--i_testset=180000 \
--i_video=180000

```

## 推理
生成评分用的数据只需要将--i_img、--i_testset和--i_video这三个参数设置成你想要每隔多少次迭代生成一次图片即可，比如想每隔18万次迭代生成一次就可以设置180000