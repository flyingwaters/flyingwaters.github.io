---
layout: post
title:  "ACL2020 Coach：A  Coarse-to-Fine Approach for Cross-Domain Slot Filling "
categories: NLP
tags:  SlotFilling
author: fly
---

* content
{:toc}





HUST 香港科技大学的一篇slot filling文章，Coach: A coarse-to-fine Approach for Cross-Domain Slot Filling，主要贡献一种template regularize 结合深度学习。和BiLSTM+CRF结合粗细粒度全面侦测，

 解决任务型对话中，槽填充种缺少训练数据的关键性问题。提出一种由粗粒度到细粒度的交叉域槽填充方法。
        - 通过侦测tokens是否为槽实体，之后预测槽实体的具体类型。
        - 另外，我们提出一个模板正则化的方法，来提高泛化鲁棒性，这种方法通过对话模板来正则化表示对话。
  实验表明，slotfiling STOA  并且 模型可以被用于交叉领域，具有比存在的baselines更好的适应性表现。

动机：虽然监督学习的槽填充具有很好的效果但是大量（substantial）的标注训练数据是必须的，这给实际应用带来巨大代价。因此我们investigate cross-domain slot filling methods，which leverage knowleage learned in the source domains and adapt the model to the target domain with a minimum number of  target domain labeled training  samples.

难点： 处理未知的（unseen) 槽类型， 这会造成分类模型无法在没有任何目标领域监督学习信号下分类。

前人工作：Bapna 2017 -zero shot Adaption 先单词级别表示后整体融合，基于整体预测slot type，易发生错误。

工作分析：in order to capture the whole slot  entity  it is pivotal for model 在源领域分享参数給所有槽类型是十分重要的，学习槽实体的通用模式。
therefore  we proposed a new cross-domain slot filing framework  called Coach，一个粗i粒度到细粒度的approach。它首先通过预测tokens是否为槽实体来粗粒度学习。
Then，it combines the features  for  each slot  entity  and  predicts the fine slot type based on the similarity with the representation of each slot type description。用这种方法避免多个预测的问题。另外，我们引入一个模板正则的方法，降低对话中槽实体的tokens灵活性，变为各种不同槽标签，并且产生正确和错误对话模板来正则化对话表示。
.
相近的idea: 粗到细的方法在NLP中，因为句法分析而闻名，通过使用粗粒度的宏观语法，减少搜索空间。我们应用这个idea 到cross-domain slot filling 来解决未知槽类型通过把槽填充分为两个步骤。
以往low-resource任务，将source domain 和 target domain的slot types设置为一致。

- Coach FrameWork 
      - BiLSTM_ CRF structure  to  predict whether tokens  are slot  entities or not
      - predict slot type ,To  generate 所有可能的slot types的表示，we use Encoder BILSTM to    
         encode the hidden states of slot entity tokens and 产生每个槽实体的表示。
      - 模板正则，许多例子中相同slot type在source和target中同时存在，然而，辨别target domain中的slot type仍然十分困难，由于variance。我们的方法中，用slot labels 替换slot entities，用encoder（BiLSTM ）来encoder 两个达向量分别为utterance 和 temnplate向量，以正常模板和utterance为正确，错误模板和uttera 为错误，生成loss训练神经网络，过程略。加大robustness of these slot types in the  target domain 。
Result： zero-shot 30.55  32.85.  35.82  37.39   20-few shot 53.6  56.53   63.17  64.27  
