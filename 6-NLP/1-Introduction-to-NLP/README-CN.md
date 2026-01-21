# 自然语言处理简介

本课概述了*自然语言处理*（NLP，属*计算语言学*的一个子领域）的简史与重要概念。

## [课前测验](https://ff-quizzes.netlify.app/en/ml/)

## 引言

NLP 是机器学习最为人熟知且已广泛进入生产软件的领域之一。

✅ 想想你每天使用的软件中，哪些可能嵌入了 NLP？常用的文字处理程序或移动应用呢？

你将学习：

- **语言的概念**：语言如何演化，以及主要的研究方向。
- **定义与概念**：了解计算机处理文本时的定义与概念，包括解析、语法、以及识别名词和动词。本课包含若干编码任务，并引入多个之后课程中会实现的重要概念。

## 计算语言学

计算语言学是一个持续数十年的研究与开发领域，探讨计算机如何与语言协作，甚至理解、翻译与交流。自然语言处理（NLP）是相关领域，聚焦计算机如何处理“自然”或人类语言。

### 例子——手机听写

如果你曾对手机语音输入而非打字，或向虚拟助手提问，你的语音会先被转换为文本，再根据你使用的语言被处理或*解析*。随后，检测到的关键词会被转化为设备可理解并执行的格式。

![comprehension](images/comprehension.png)
> 语言理解真的很难！图片作者 [Jen Looper](https://twitter.com/jenlooper)

### 这项技术如何实现？

因为有人编写了执行此任务的计算机程序。数十年前，科幻作家预言人们会主要通过语音与计算机交流，且计算机总能准确理解人类意图。遗憾的是，这个问题比许多人想象的更难；即便今天理解更深入，要实现“完美”的自然语言处理以真正理解句子含义，仍面临巨大挑战，尤其在理解幽默或检测讽刺情绪时。

此时你或许想起学校里学习语法的课程。在一些国家，学生会将语法和语言学作为独立科目学习；而在许多国家，这些主题是语言学习的一部分：小学阶段学习母语的读写，可能在中学阶段学习第二语言。即使你无法熟练区分名词、动词或副词、形容词，也不必担心！

如果你曾为区分*一般现在时*与*现在进行时*而苦恼，你绝非孤例。这对很多人来说都很难，即便是母语者。好消息是，计算机非常擅长应用形式化规则，你将学习如何编写代码，使其像人类一样*解析*句子。更大的挑战是理解句子的*含义*和*情感*。

## 先决条件

本课的主要先决条件是能够阅读并理解课程所用语言。本课没有数学题或方程。虽然作者以英语撰写本课，但也被翻译成其他语言，因此你可能正在阅读译本。文中举例时会使用多种语言（用于比较不同语言的语法规则）。这些示例*并未*翻译，但其说明文本已经翻译，因此意义应当清晰。

在编码任务中，你将使用 Python，示例基于 Python 3.8。

在本节中，你需要并将使用：

- **Python 3 理解能力**：熟悉 Python 3 编程语言，本课涉及输入、循环、文件读取与数组。
- **Visual Studio Code + 扩展**：我们将使用 Visual Studio Code 及其 Python 扩展，你也可选择其他 Python IDE。
- **TextBlob**：[TextBlob](https://github.com/sloria/TextBlob) 是一个简化的 Python 文本处理库。请按照 TextBlob 网站上的说明进行安装（并按下方所示安装语料）：

   ```bash
   pip install -U textblob
   python -m textblob.download_corpora
   ```

> 💡 提示：你可以直接在 VS Code 环境中运行 Python。查阅[文档](https://code.visualstudio.com/docs/languages/python?WT.mc_id=academic-77952-leestott)获取更多信息。

## 与机器对话

让计算机理解人类语言的历史可以追溯数十年，最早考虑自然语言处理的科学家之一是*阿兰·图灵*。

### “图灵测试”

上世纪 50 年代，图灵研究*人工智能*时提出：是否可以设计一种对话测试，让人与计算机（通过文字通信）进行对话，而人类无法确定对方是计算机还是人类？

如果经过一定时间的对话后，人类仍无法判断回答者是否为计算机，那么计算机是否可以被认为在“思考”？

### 灵感来源——“模仿游戏”

该想法来源于一款名为*“模仿游戏”*的聚会游戏：一名审问者独自待在房间内，需要判断另一个房间中两人的性别。审问者可发送字条，并尝试提出问题，通过回答来辨别身份。当然，房间内的玩家会尽力欺骗或迷惑审问者，同时让回答看似诚实。

### Eliza 的诞生

1960 年代，MIT 科学家 *Joseph Weizenbaum* 开发了[*Eliza*](https://wikipedia.org/wiki/ELIZA)，一个看似理解人类答案的计算机“治疗师”。Eliza 能解析句子、识别特定的语法结构和关键词，并给出合乎情理的回答，但它并不能真正*理解*句子。如果 Eliza 收到“**I am** <u>sad</u>”的句式，可能通过调整词序和词语形成回答：“How long have **you been** <u>sad</u>”。

这种方式让人觉得 Eliza 理解了陈述并提出跟进问题，但实际上它只是改变时态并添加一些词。如果 Eliza 无法找到可匹配的关键词，就会给出一个适用于多种陈述的随机回答。Eliza 很容易被捉弄，例如用户输入“**You are** a <u>bicycle</u>”，它可能回答“（中文版保留原结构）How long have **I been** a <u>bicycle</u>?”，而不是更合理的回应。

[![Chatting with Eliza](https://img.youtube.com/vi/RMK9AphfLco/0.jpg)](https://youtu.be/RMK9AphfLco "Chatting with Eliza")

> 🎥 点击上图观看原始 ELIZA 程序的视频

> 注意：如果你拥有 ACM 账号，可阅读 1966 年发表的 [Eliza](https://cacm.acm.org/magazines/1966/1/13317-elizaa-computer-program-for-the-study-of-natural-language-communication-between-man-and-machine/abstract) 原始描述。或者在 [Wikipedia](https://wikipedia.org/wiki/ELIZA) 上了解 Eliza。

## 练习——编写基础会话机器人

像 Eliza 一样，会话机器人会获取用户输入，并看似理解且作出智能回应。与 Eliza 不同，我们的机器人没有大量规则，仅有一个能力：借助随机回应，在几乎任何简单对话中保持交流继续。

### 计划

构建会话机器人时的步骤：

1. 输出指令，告知用户如何与机器人交互
2. 启动循环
   1. 接收用户输入
   2. 若用户请求退出，则结束
   3. 处理输入并确定回应（此处从通用回答列表中随机选择）
   4. 打印回应
3. 回到步骤 2

### 构建机器人

接下来创建机器人。首先定义若干短语。

1. 使用下列随机回复，在 Python 中自行创建该机器人：

    ```python
    random_responses = ["That is quite interesting, please tell me more.",
                        "I see. Do go on.",
                        "Why do you say that?",
                        "Funny weather we've been having, isn't it?",
                        "Let's change the subject.",
                        "Did you catch the game last night?"]
    ```

    以下为示例输出供参考（以 `>` 开头的行为用户输入）：

    ```output
    Hello, I am Marvin, the simple robot.
    You can end this conversation at any time by typing 'bye'
    After typing each answer, press 'enter'
    How are you today?
    > I am good thanks
    That is quite interesting, please tell me more.
    > today I went for a walk     
    Did you catch the game last night?
    > I did, but my team lost
    Funny weather we've been having, isn't it?
    > yes but I hope next week is better
    Let's change the subject.
    > ok, lets talk about music
    Why do you say that?
    > because I like music!
    Why do you say that?
    > bye
    It was nice talking to you, goodbye!
    ```

    这里提供[一种可能的解决方案](https://github.com/microsoft/ML-For-Beginners/blob/main/6-NLP/1-Introduction-to-NLP/solution/bot.py)

    ✅ 停下来思考：

    1. 这些随机回复能“骗过”别人，让他们认为机器人真正理解了他们吗？
    2. 要让机器人更有效，需要哪些特性？
    3. 如果机器人真的能理解句子含义，它是否需要“记住”对话中前面句子的含义？

---

## 🚀 挑战

从以上“停下来思考”中的任意一项着手，尝试用代码实现或用伪代码写出方案。

下一课你将学习更多解析自然语言与机器学习的方法。

## [课后测验](https://ff-quizzes.netlify.app/en/ml/)

## 复习与自学

查看下列参考资料，作为进一步阅读的机会。

### 参考文献

1. Schubert, Lenhart, "Computational Linguistics", *The Stanford Encyclopedia of Philosophy* (2020 年春季版)，Edward N. Zalta（编），URL = <https://plato.stanford.edu/archives/spr2020/entries/computational-linguistics/>。
2. Princeton University "About WordNet." [WordNet](https://wordnet.princeton.edu/). Princeton University. 2010.

## 作业

[寻找一个机器人](assignment.md)
