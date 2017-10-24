# CMOS_callreason
  
  本项目实现中移在线来电原因单标签分类。

---
# 使用的方法

来电原因分析分为一级标签分类以及二级标签分类，目前实现的方法中将两个标签分类作为完全独立的任务。  
一级标签分类最终使用fasttext完成分类，二级标签分类使用sklearn的linearSvc完成分类。  

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

---
# 模型训练
## 数据文件
模型训练和测试时要求输入文件按照预定的格式存储，文件示例可参考TrainModel/DataUtil/sk_example.txt, 每行由tab划分为四列，第一列为通话的标识信息，实际可为任意不含有tab的数据，第二列、第三列分别是一级分类标签和二级分类标签，第三列为分词后的通话内容

## 训练模型
模型训练参考TrainFasttext、TrainSvcModel下的train.sh文件，在训练前根据实际情况修改每个目录下的config目录下的配置文件中的目标文件路径、模型文件名、训练文件、测试文件、测试结果文件等相关信息，然后直接运行train.sh文件即可

---
# 模型预测
模型预测时一级分类使用的是fasttext，二级分类使用的是linearsvc，但是目前的代码中要求两个方法都提供一级、二级分类模型，后续可将相应的地方进行修改。  
目前有三个用于预测的python文件，分别对应三种不同格式的输入数据。  
## classifyResultFile.py
该文件用于处理讯飞转写引擎转写的以result.txt文件存储的文本数据
## classifyXmlDataFile.py
该文件用于处理含有解析xml的结果文件的预测，文件格式为record_key + tab + data_info_json，其中data_info_json是以json格式存储的对话内容,具体格式可参考BaseUtil/data_info_json.txt
## classifyXmlDataWithTagId.py
该文件处理语音转写引擎转写的xml文件，文件格式参考BaseUtil/1245079.xml

## 预测
以文件进行输入，对文件进行预测，运行方法可参考start.sh文件
