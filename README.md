# Shape Robust Text Detection with Progressive Scale Expansion Network

## Requirements
* Python 3.6
* PyTorch v1.0
* pyclipper
* Polygon2
* OpenCV 3+ (for c++ version pse)

## Data Preparation

```
image
│   1.jpg
│   2.jpg   
│		...
label
│   gt_1.txt
│   gt_2.txt
|		...
```

注意：

1、label要和image对应，且命名加gt_

2、txt中标签格式为：x1,y1,x2,y2,x3,y3,x4,y4,label_name(可有可无)，以左上角开始逆时针四个点坐标，最后name可有可无。

## Training

```
step1:修改dataset/icdar2015_loader.py 中训练测试图像及label路径
step2:执行命令 CUDA_VISIBLE_DEVICES=0,1 python train_ic15.py 
注意训练命令参数可选：
--arch 默认resnt50,可选resnet18、resnet34、resnet50、resnet101、resnet152
--img_size 默认640
--n_epoch  迭代步数，默认600
--schedule 调整学习步数，默认200-400，输入int型
--batch_size 默认16
--lr 学习率，默认0.001
--checkpoint 模型保存路径，默认保存在checpoint下
```

## Testing
```
step1:修改dataset/icdar2015_test_loader.py 中训练测试图像及label路径
step2:执行命令 CUDA_VISIBLE_DEVICES=0 python test_ic15.py --scale 1 --resume [path of model]
注意训练命令参数可选：
--arch 默认resnt50,可选resnet18、resnet34、resnet50、resnet101、resnet152
--resume 模型路径
--long_size 输入尺寸，默认2240
```



