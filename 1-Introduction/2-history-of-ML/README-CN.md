# 机器学习的历史

![机器学习历史概述手绘笔记](../../sketchnotes/ml-history.png)
> 手绘笔记由 [Tomomi Imura](https://www.twitter.com/girlie_mac) 绘制

## [课前测验](https://ff-quizzes.netlify.app/en/ml/)

---

[![ML for beginners - History of Machine Learning](https://img.youtube.com/vi/N6wxM4wZ7V0/0.jpg)](https://youtu.be/N6wxM4wZ7V0 "ML for beginners - History of Machine Learning")

> 🎥 点击上方图片观看本课程的短视频。

在本课中，我们将回顾机器学习和人工智能历史上的重要里程碑。

人工智能（AI）作为一个领域的历史与机器学习的历史紧密交织，因为支撑机器学习的算法和计算进步推动了人工智能的发展。值得记住的是，虽然这些领域作为独立的研究领域在20世纪50年代开始形成，但重要的[算法、统计、数学、计算和技术发现](https://wikipedia.org/wiki/Timeline_of_machine_learning)早于这个时代并与之重叠。事实上，人们思考这些问题已有[数百年](https://wikipedia.org/wiki/History_of_artificial_intelligence)：本文讨论了"会思考的机器"这一概念的历史思想基础。

---
## 重要发现

- 1763年、1812年 [贝叶斯定理](https://wikipedia.org/wiki/Bayes%27_theorem)及其前身。该定理及其应用是推理的基础，描述了基于先验知识的事件发生概率。
- 1805年 法国数学家阿德里安-马里·勒让德提出[最小二乘法](https://wikipedia.org/wiki/Least_squares)。这一理论将在我们的回归单元中学习，有助于数据拟合。
- 1913年 [马尔可夫链](https://wikipedia.org/wiki/Markov_chain)，以俄罗斯数学家安德烈·马尔可夫命名，用于描述基于先前状态的可能事件序列。
- 1957年 [感知器](https://wikipedia.org/wiki/Perceptron)是由美国心理学家弗兰克·罗森布拉特发明的一种线性分类器，它为深度学习的进步奠定了基础。

---

- 1967年 [最近邻算法](https://wikipedia.org/wiki/Nearest_neighbor)最初是为路线规划设计的算法。在机器学习中，它用于检测模式。
- 1970年 [反向传播](https://wikipedia.org/wiki/Backpropagation)用于训练[前馈神经网络](https://wikipedia.org/wiki/Feedforward_neural_network)。
- 1982年 [循环神经网络](https://wikipedia.org/wiki/Recurrent_neural_network)是从前馈神经网络衍生出的人工神经网络，可以创建时序图。

✅ 做一些研究。在机器学习和人工智能的历史中，还有哪些日期是关键的？

---
## 1950年：会思考的机器

艾伦·图灵，一位真正杰出的人物，在[2019年被公众投票](https://wikipedia.org/wiki/Icons:_The_Greatest_Person_of_the_20th_Century)选为20世纪最伟大的科学家，他被认为帮助奠定了"会思考的机器"这一概念的基础。他与质疑者抗争，并通过创建[图灵测试](https://www.bbc.com/news/technology-18475646)来寻求这一概念的经验证据，你将在我们的NLP课程中探索这个测试。

---
## 1956年：达特茅斯夏季研究项目

"达特茅斯人工智能夏季研究项目是人工智能作为一个领域的开创性事件"，正是在这里，"人工智能"这个术语被首次提出（[来源](https://250.dartmouth.edu/highlights/artificial-intelligence-ai-coined-dartmouth)）。

> 学习的每个方面或智能的任何其他特征原则上都可以被精确描述，以至于可以制造一台机器来模拟它。

---

首席研究员、数学教授约翰·麦卡锡希望"基于这样一个猜想继续推进：学习的每个方面或智能的任何其他特征原则上都可以被精确描述，以至于可以制造一台机器来模拟它。"参与者还包括该领域的另一位杰出人物马文·明斯基。

这次研讨会被认为启动并推动了多项讨论，包括"符号方法的兴起、专注于有限领域的系统（早期专家系统），以及演绎系统与归纳系统的比较。"（[来源](https://wikipedia.org/wiki/Dartmouth_workshop)）

---
## 1956 - 1974年："黄金时代"

从20世纪50年代到70年代中期，人们对人工智能能够解决许多问题抱有很高的期望。1967年，马文·明斯基自信地表示："在一代人的时间内……创造'人工智能'的问题将基本得到解决。"（Minsky, Marvin (1967), Computation: Finite and Infinite Machines, Englewood Cliffs, N.J.: Prentice-Hall）

自然语言处理研究蓬勃发展，搜索技术得到改进并变得更加强大，"微世界"的概念被创造出来，在这些微世界中，可以使用简单的语言指令完成简单任务。

---

研究得到了政府机构的大量资助，计算和算法取得了进步，智能机器的原型被建造出来。其中一些机器包括：

* [Shakey机器人](https://wikipedia.org/wiki/Shakey_the_robot)，它可以移动并"智能地"决定如何执行任务。

    ![Shakey，一个智能机器人](images/shakey.jpg)
    > 1972年的Shakey

---

* Eliza，一个早期的"聊天机器人"，可以与人交谈并充当原始的"治疗师"。你将在NLP课程中了解更多关于Eliza的内容。

    ![Eliza，一个聊天机器人](images/eliza.png)
    > Eliza的一个版本，一个聊天机器人

---

* "积木世界"是微世界的一个例子，其中积木可以被堆叠和分类，并可以测试教机器做决策的实验。使用[SHRDLU](https://wikipedia.org/wiki/SHRDLU)等库构建的进步推动了语言处理的发展。

    [![用SHRDLU实现的积木世界](https://img.youtube.com/vi/QAJz4YKUwqw/0.jpg)](https://www.youtube.com/watch?v=QAJz4YKUwqw "blocks world with SHRDLU")

    > 🎥 点击上方图片观看视频：用SHRDLU实现的积木世界

---
## 1974 - 1980年："人工智能寒冬"

到20世纪70年代中期，制造"智能机器"的复杂性被低估，而且鉴于当时可用的计算能力，其前景被过度夸大，这一点变得越来越明显。资金枯竭，对该领域的信心下降。影响信心的一些问题包括：

---
- **局限性**。计算能力太有限了。
- **组合爆炸**。随着对计算机要求的增加，需要训练的参数数量呈指数级增长，而计算能力和性能却没有同步发展。
- **数据匮乏**。数据的匮乏阻碍了算法的测试、开发和改进过程。
- **我们问对问题了吗？** 人们开始质疑所提出的问题本身。研究人员开始受到对其方法的批评：
  - 图灵测试受到质疑，其中包括"中文房间理论"，该理论认为"对数字计算机编程可能使其看起来理解语言，但不能产生真正的理解。"（[来源](https://plato.stanford.edu/entries/chinese-room/)）
  - 将"治疗师"ELIZA等人工智能引入社会的伦理问题受到挑战。

---

与此同时，各种人工智能学派开始形成。["粗犷派"与"简洁派"人工智能](https://wikipedia.org/wiki/Neats_and_scruffies)实践之间建立了二分法。_粗犷派_实验室花费数小时调整程序，直到获得所需的结果。_简洁派_实验室"专注于逻辑和形式化问题求解"。ELIZA和SHRDLU是著名的_粗犷派_系统。在20世纪80年代，随着使机器学习系统可复现的需求出现，_简洁派_方法逐渐占据主导地位，因为其结果更具可解释性。

---
## 20世纪80年代：专家系统

随着该领域的发展，其对商业的好处变得更加明显，在20世纪80年代，"专家系统"也开始普及。"专家系统是最早真正成功的人工智能（AI）软件形式之一。"（[来源](https://wikipedia.org/wiki/Expert_system)）

这种类型的系统实际上是_混合_的，部分由定义业务需求的规则引擎组成，以及利用规则系统推导新事实的推理引擎。

这个时代也见证了神经网络越来越受到关注。

---
## 1987 - 1993年：人工智能"冷却期"

专用专家系统硬件的激增产生了一个不幸的后果——变得过于专业化。个人电脑的兴起也与这些大型、专业化、集中式的系统形成了竞争。计算的民主化已经开始，并最终为现代大数据的爆发铺平了道路。

---
## 1993 - 2011年

这个时期见证了机器学习和人工智能的新纪元，能够解决早期因数据和计算能力不足而导致的一些问题。数据量开始快速增长并变得更加广泛可用，无论好坏，特别是随着2007年左右智能手机的出现。计算能力呈指数级扩展，算法也随之发展。随着过去自由放任的时代开始凝聚成一门真正的学科，该领域开始走向成熟。

---
## 现在

今天，机器学习和人工智能几乎触及我们生活的方方面面。这个时代需要我们仔细理解这些算法对人类生活的风险和潜在影响。正如微软的布拉德·史密斯所说："信息技术引发的问题触及隐私和言论自由等基本人权保护的核心。这些问题加重了创造这些产品的科技公司的责任。在我们看来，它们也呼吁深思熟虑的政府监管，以及围绕可接受使用的规范的制定。"（[来源](https://www.technologyreview.com/2019/12/18/102365/the-future-of-ais-impact-on-society/)）

---

未来会怎样还有待观察，但重要的是理解这些计算机系统以及它们运行的软件和算法。我们希望本课程能帮助你获得更好的理解，以便你能够自己做出判断。

[![深度学习的历史](https://img.youtube.com/vi/mTtDfKgLm54/0.jpg)](https://www.youtube.com/watch?v=mTtDfKgLm54 "The history of deep learning")
> 🎥 点击上方图片观看视频：Yann LeCun在这次讲座中讨论深度学习的历史

---
## 🚀 挑战

深入研究其中一个历史时刻，了解更多关于背后人物的故事。这里有许多迷人的人物，没有任何科学发现是在文化真空中创造的。你发现了什么？

## [课后测验](https://ff-quizzes.netlify.app/en/ml/)

---
## 复习与自学

以下是一些可以观看和收听的内容：

[Amy Boyd讨论人工智能演变的播客](http://runasradio.com/Shows/Show/739)

[![Amy Boyd讲述人工智能的历史](https://img.youtube.com/vi/EJt3_bFYKss/0.jpg)](https://www.youtube.com/watch?v=EJt3_bFYKss "The history of AI by Amy Boyd")

---

## 作业

[创建时间线](assignment.md)
