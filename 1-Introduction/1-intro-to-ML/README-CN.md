# 机器学习入门

## [课前测验](https://ff-quizzes.netlify.app/en/ml/)

---

[![ML for beginners - Introduction to Machine Learning for Beginners](https://img.youtube.com/vi/6mSx_KJxcHI/0.jpg)](https://youtu.be/6mSx_KJxcHI "ML for beginners - Introduction to Machine Learning for Beginners")

> 🎥 点击上方图片观看本课程的短视频。

欢迎来到这门面向初学者的经典机器学习课程！无论你是完全的新手，还是想要温习某个领域的资深ML从业者，我们都很高兴你能加入！我们希望为你的ML学习之旅创建一个友好的起点，并乐于评估、回应和采纳你的[反馈](https://github.com/microsoft/ML-For-Beginners/discussions)。

[![Introduction to ML](https://img.youtube.com/vi/h0e2HAPTGF4/0.jpg)](https://youtu.be/h0e2HAPTGF4 "Introduction to ML")

> 🎥 点击上方图片观看视频：MIT的John Guttag介绍机器学习

---
## 机器学习入门准备

在开始本课程之前，你需要配置好电脑，以便能够在本地运行notebook。

- **通过这些视频配置你的机器**。使用以下链接学习[如何安装Python](https://youtu.be/CXZYvNRIAKM)以及[如何设置开发用的文本编辑器](https://youtu.be/EU8eayHWoZg)。
- **学习Python**。建议你对[Python](https://docs.microsoft.com/learn/paths/python-language/?WT.mc_id=academic-77952-leestott)有基本的了解，这是一种对数据科学家非常有用的编程语言，我们在本课程中会使用它。
- **学习Node.js和JavaScript**。我们在本课程中构建web应用时也会用到JavaScript几次，因此你需要安装[node](https://nodejs.org)和[npm](https://www.npmjs.com/)，并且需要[Visual Studio Code](https://code.visualstudio.com/)来进行Python和JavaScript开发。
- **创建GitHub账户**。既然你在[GitHub](https://github.com)上找到了我们，你可能已经有账户了，如果没有，请创建一个并fork这个课程以供你自己使用。（也欢迎给我们一个Star 😊）
- **探索Scikit-learn**。熟悉[Scikit-learn](https://scikit-learn.org/stable/user_guide.html)，这是我们在课程中引用的一套ML库。

---
## 什么是机器学习？

"机器学习"这个术语是当今最流行和最常用的术语之一。如果你对技术有一定的了解，无论你在哪个领域工作，你很可能至少听说过这个术语。然而，对于大多数人来说，机器学习的机制是一个谜。对于机器学习初学者来说，这个主题有时会让人感到不知所措。因此，理解机器学习到底是什么，并通过实际例子一步一步地学习它是很重要的。

---
## 炒作曲线

![ml hype curve](images/hype.png)

> Google趋势显示了"机器学习"这个术语近期的"炒作曲线"

---
## 神秘的宇宙

我们生活在一个充满迷人奥秘的宇宙中。像斯蒂芬·霍金、阿尔伯特·爱因斯坦等伟大的科学家们毕生致力于寻找有意义的信息，揭示我们周围世界的奥秘。这是人类学习的本性：人类的孩子在成长过程中，年复一年地学习新事物，揭示他们所处世界的结构。

---
## 儿童的大脑

儿童的大脑和感官感知周围环境的事实，逐渐学习生活中隐藏的模式，这帮助儿童制定逻辑规则来识别已学习的模式。人脑的学习过程使人类成为这个世界上最复杂的生物。通过不断发现隐藏的模式，然后在这些模式上进行创新，使我们在一生中不断变得更好。这种学习能力和进化能力与一个叫做[大脑可塑性](https://www.simplypsychology.org/brain-plasticity.html)的概念有关。从表面上看，我们可以在人脑的学习过程和机器学习的概念之间找到一些相似之处。

---
## 人脑

[人脑](https://www.livescience.com/29365-human-brain.html)从现实世界中感知事物，处理感知到的信息，做出理性决策，并根据情况执行某些动作。这就是我们所说的智能行为。当我们将这种智能行为过程的模拟编程到机器中时，它被称为人工智能（AI）。

---
## 一些术语

虽然这些术语可能会混淆，但机器学习（ML）是人工智能的一个重要子集。**ML关注的是使用专门的算法从感知到的数据中发现有意义的信息，找到隐藏的模式，以支持理性决策过程**。

---
## AI、ML、深度学习

![AI, ML, deep learning, data science](images/ai-ml-ds.png)

> 展示AI、ML、深度学习和数据科学之间关系的图表。信息图由[Jen Looper](https://twitter.com/jenlooper)制作，灵感来源于[这张图](https://softwareengineering.stackexchange.com/questions/366996/distinction-between-ai-ml-neural-networks-deep-learning-and-data-mining)

---
## 要涵盖的概念

在本课程中，我们只会涵盖初学者必须了解的机器学习核心概念。我们主要使用Scikit-learn来介绍我们所说的"经典机器学习"，这是一个许多学生用来学习基础知识的优秀库。要理解人工智能或深度学习的更广泛概念，机器学习的坚实基础知识是不可或缺的，因此我们希望在这里提供这些知识。

---
## 在本课程中你将学习：

- 机器学习的核心概念
- ML的历史
- ML与公平性
- 回归ML技术
- 分类ML技术
- 聚类ML技术
- 自然语言处理ML技术
- 时间序列预测ML技术
- 强化学习
- ML的实际应用

---
## 我们不会涵盖的内容

- 深度学习
- 神经网络
- AI

为了提供更好的学习体验，我们将避免神经网络的复杂性、使用神经网络进行多层模型构建的"深度学习"以及AI，我们将在另一个课程中讨论这些内容。我们还将提供即将推出的数据科学课程，专注于这个更大领域的该方面。

---
## 为什么要学习机器学习？

从系统的角度来看，机器学习被定义为创建能够从数据中学习隐藏模式的自动化系统，以帮助做出智能决策。

这一动机大致受到人脑如何根据从外部世界感知到的数据学习某些事物的启发。

✅ 花一分钟思考一下，为什么企业会想尝试使用机器学习策略，而不是创建基于硬编码规则的引擎。

---
## 机器学习的应用

机器学习的应用现在几乎无处不在，就像我们社会中流动的数据一样普遍，这些数据由我们的智能手机、联网设备和其他系统产生。考虑到最先进的机器学习算法的巨大潜力，研究人员一直在探索它们解决多维度和跨学科现实问题的能力，并取得了很好的成果。

---
## 应用ML的例子

**你可以在许多方面使用机器学习**：

- 根据患者的病史或报告预测疾病的可能性。
- 利用天气数据预测天气事件。
- 理解文本的情感。
- 检测假新闻以阻止宣传的传播。

金融、经济学、地球科学、太空探索、生物医学工程、认知科学，甚至人文学科领域都已采用机器学习来解决其领域中艰巨的、数据处理繁重的问题。

---
## 结论

机器学习通过从真实世界或生成的数据中发现有意义的洞察来自动化模式发现过程。它已被证明在商业、医疗保健和金融应用等领域具有很高的价值。

在不久的将来，由于机器学习的广泛采用，理解机器学习的基础知识将成为任何领域人士的必备技能。

---
# 🚀 挑战

在纸上或使用[Excalidraw](https://excalidraw.com/)等在线应用，画出你对AI、ML、深度学习和数据科学之间区别的理解。添加一些关于这些技术各自擅长解决的问题的想法。

# [课后测验](https://ff-quizzes.netlify.app/en/ml/)

---
# 复习与自学

要了解更多关于如何在云端使用ML算法的信息，请参阅这个[学习路径](https://docs.microsoft.com/learn/paths/create-no-code-predictive-models-azure-machine-learning/?WT.mc_id=academic-77952-leestott)。

参加关于ML基础知识的[学习路径](https://docs.microsoft.com/learn/modules/introduction-to-machine-learning/?WT.mc_id=academic-77952-leestott)。

---
# 作业

[开始行动](assignment.md)
