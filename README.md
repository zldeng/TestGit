# CMOS_callreason
  
  本项目实现中移在线来电原因单标签分类。

---
# 使用的方法

来电原因分析分为一级标签分类以及二级标签分类，目前实现的方法中将两个标签分类作为完全独立的任务。 一级标签分类最终使用fasttext完成分类，二级标签分类使用sklearn的linearSvc完成分类。  

---
# 目录说明
## TrainModel
该目录下的代码用于训练模型，包括fasttext、linerSvc两个模型
## Fastext
该目录是使用Fasttext模型进行分类预测的相关代码
## LinearSvc
该目录是使用linearSvc模型进行分类预测的相关代码
---
# 算法说明
来电原因分析分为一级标签分类以及二级标签分类，目前实现的方法中将两个标签分类作为完全独立的任务。 一级标签分类最终使用fasttext完成分类，二级标签分类使用sklearn的linearSvc完成分类。
