# MultiLabelsCallReason
  
  本项目实现中移在线来电原因多标签分类。

---
# 使用的方法

来电原因分析分为一级标签分类以及二级标签分类，目前实现的方法中将两个标签分类作为完全独立的任务。  
两类标签的分类均使用sklearn中的OneVsRest模块完成，底层分类器使用linearSvc分类器。  

---
# 目录说明
## gridSearchModel
该目录下的代码用于搜索模型的最佳参数，使用方法见目录下的grid_search.sh文件
## conf
该目录是项目的配置文件，主要配置项有模型文件路径、文件名、分类标签以及对应的id等信息
## sample/xml
该目录是作为输入文件的xml文件示例

---
# 模型训练
## 数据文件
模型训练和测试时要求输入文件按照预定的格式存储，文件示例可参考sample/sk_example.txt, 每行由tab划分为三列，第一列为通话的标识信息，实际可为任意不含有tab的数据，第二列为分类标签信息，格式为json list，第三列为分词后的通话内容

## 训练模型
模型训练参照train.sh文件，需要根据实际情况修改相关参数，主要包括训练、测试文件配置、模型文件保存路径等相关信息

---
# 模型评估
模型训练完成后可使用测试文件测试模型在测试集数据上的分类效果。  
测试时使用eval.sh文件，根据实际情况修改eval.sh文件中的相关参数即可

# 模型预测
## 测试预测接口
测试分类模型的预测接口可使用test.py文件，输入文件的格式为每行一个对话内容，对话内容为空格分割的分词后的文本，具体文件格式可参照sample/test.sample文件

## 批量文件预测
以xml文件进行输入，一次一个文件夹下的多个xml文件，运行方法可参考clf_xml.sh脚本
