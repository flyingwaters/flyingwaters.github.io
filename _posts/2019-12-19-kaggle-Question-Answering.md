---
layout: post
title:  "TF2.0 kaggle Question Answering"
categories: NLP
tags:  DL  NLP  
author: fly
---
# TF2.0 kaggle Question Answering 
### 1. 审题
    开放域问答系统， QA系统模仿人们怎样通过阅读互联网查找答案，并且返回一般答案。

    现有的自然的语言模型集中于从一篇短小的文章抽取内容而不是通过阅读一整篇内容获取合适的上下文语境。结果，这个回答是复杂的并且冗长的。一个好的答案，succinct（简洁）和 revelant关联的

    在这个比赛中，你的目标是预测短的和长答案， 回答真实的关于wikipedia问题，数据集是Google Natural Questions， 包含它自己的独特的私有测试集。一个可视化的例子显示了长的 和 短的答案，为了奖励top teams， 有一个特别的awards for using Tensorflow 2.0 APIs

    如果成功， 这个challenge 将会激励更有效率和健壮的QA系统.
    



    
### 2.Tensorflow
    tensorflow 是一个针对机器学习的开放资源平台，在TF2.0 中 tf.keras 是更被推荐选择的高层API for Tensorflow ，为了使得模型的建立更加容易直觉地进步， 同时促进问答系统进步。

### 3. Data Description
    Data format   Each sample contains a Wikipedia article, a related question  
question|answer
--|:--:|--:
Wikipedia| related question
Wikipedia| related question
Wikipedia| related question

Waiting  for download data!!!!!!!!!!!!!!!!!!!!
