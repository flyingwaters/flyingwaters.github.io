---
layout: post
title: "对话系统中Data Augmentation"
categories: NLP
tags:  Data Augmentation
author: fly
---

* content
{:toc}

在实际的AI的落地产品中,低资源的问题是一直存在的，在各种NLP的应用场景下。中文在语言中应该说标注数据是相对较多的，仅仅低于英语的标注资源。但是实际落地的项目中，低资源的难题依然困扰着算法工程师和相关从业人员。以智能对话系统的意图识别和槽填充为例子。也就是Slot filling and 意图识别。这两个任务分别数于NLP的四大基本任务中的序列标注和文本分类。也是我近期项目中遇到的问题，实际场景下的问题是远离paper的，但是paper中的低资源技巧十分有借鉴意义。












（1） 构建一定量的意图识别的train data。

现实中的每个意图
（1）缴纳公积金的注意事项？
（2）缴纳住房公积金的相关注意事项
（3）请问公积金缴纳的注意事项有什么？
（4）公积金缴纳需要注意什么？

如何落地解决的意图识别的问题，
（1）规则模板匹配，需要精细人工参与，优点准确率高，缺点工时大，容易产生交叉。
（2）数据驱动的机器学习，需要大规模train数据来拟合，缺点low-resource，需要较高准确率，有时误判
2018年后，实用中大厂，通常（1）和（2）结合。也有追求高精准度而只用（1）。

如何解决低资源困扰？
总结几个Slot Filling任务的Data augmentation，后续接普适的NLP data augmentation。

从下面的论文入手，总结几份相关的paper工作。由于slot filling 的序列标注任务的特殊性，因此
多采用generative model 的方法进行。
AAAI 上的文章，哈工大的工作
（1）C2C-GenDA：Cluster-to-Cluster Generation for Data Augmentation of slot filling
解决的问题点
(1)Difficult point to solve. 
different DA works that reconstruct utterances one by one independently

其他参考文献:
(2) slot filling state-of-the-art data augmentation works on generative methods
    
(1)  Shin, Yoo, and Lee 2019

1.1--(Shin,Y.；Yoo，K.M.;and Lee,S.-G.2019. Utterance Generation with Variational Auto-Encoder for Slot Filling in Spoken Language Understanding. IEEE Signal Processing Letters)        

(2) Yoo 2020; Hou et al. 2018; Kurata, Xiang, and Zhou 2016<br/>
    2.1--(Yoo, K. M. 2020. Deep Generative Data Augmentation for 
Natural Language Processing. Ph.D. thesis, Seoul National University. ）<br/>
    2.2--(Hou, Y.; Liu, Y.; Che, W.; and Liu, T. 2018. Sequence-to
Sequence Data Augmentation for Dialogue Language Understanding. In Proc. of COLING, 1234–1245.)<br/>
    2.3--(Kurata, G.; Xiang, B.; and Zhou, B. 2016. Labeled Data 
Generation with Encoder-Decoder LSTM for Semantic Slot Filling. In Proc. of INTERSPEECH, 725–729. )<br/>

(#3) The Problems  

 these generative method tends to generate duplicated utterances, because they can only consider the expression variance between one input-output pair at a time<br/>

 these defects can be easily avoided by breaking the shackles of current one-by-one augmentation paradigm and considering the extensive instance relations during generation.<br/>
 
效果大概，100一个类别和slot filling 可以达到提升5%点左右<br/>
