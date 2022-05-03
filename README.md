# Classification-of-strawberry-pests-and-diseases

## 本项目使用深度学习模型对草莓病虫害疾病进行识别

## 项目部分代码参考地址

<https://github.com/WZMIAOMIAO/deep-learning-for-image-processing>

## 环境配置

* Python 3.8
* Pytorch 1.10.1
* Ubuntu
* AutoGluon 0.4.0
* TensorFlow 2.7

## 文件结构：
```
  ├── backbone: 特征提取网络，可以根据自己的要求选择
  ├── network_files: Faster R-CNN网络（包括Fast R-CNN以及RPN等模块）
  ├── train_utils: 训练验证相关模块（包括cocotools）
  ├── my_dataset.py: 自定义dataset用于读取VOC数据集
  ├── train_mobilenet.py: 以MobileNetV2做为backbone进行训练
  ├── train_resnet50_fpn.py: 以resnet50+FPN做为backbone进行训练
  ├── train_multi_GPU.py: 针对使用多GPU的用户使用
  ├── predict.py: 简易的预测脚本，使用训练好的权重进行预测测试
  ├── validation.py: 利用训练好的权重验证/测试数据的COCO指标，并生成record_mAP.txt文件
  └── pascal_voc_classes.json: pascal_voc标签文件
```

## 使用的模型

1. Vision Transformer

2. Swin Transformer

3. Resnet50

4. GoogleNet

5. VGG19

6. VGG16

## 数据来源

通过爬虫爬取各大农业咨询网站数据，获得**32**种不同的草莓病虫害的图像数据。
<!-- ![草莓疾病——冻害](Example.jpg =100x100)  -->
 <img src="Example.jpg" width = "300" height = "200" alt="草莓疾病——冻害" align=center />

## 不同模型精度对比

|模型|调参方法|精度|
|:------:|:------:|:------:|
|Vision Transformer|AutoGluon自动调参|90.7%|
|Swin Transformer|AutoGluon自动调参|80.3%|
|Resnet50|AutoGluon自动调参|78.56%|
|VGG19|AutoGluon自动调参|74.25%|
|VGG16|AutoGluon自动调参|75.07%|
|Vision Transformer|手动调参|71.7%|
|Swin Transformer|手动调参|70.3%|
|Resnet50|手动调参|65.16%|
|VGG19|手动调参|64.32%|
|VGG16|手动调参|65.14%|

## 精度最高的模型训练策略

1. 使用大数据集进行预训练
2. 在精选数据集上再进行训练

