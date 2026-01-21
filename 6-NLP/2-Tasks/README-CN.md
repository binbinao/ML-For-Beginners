# 自然语言处理常见任务与技术

对于大多数*自然语言处理*任务，待处理的文本必须被分解、检查，并将其结果存储或与规则和数据集进行交叉引用。这些任务使程序员能够从文本中提取*含义*或*意图*，或者仅仅统计词和术语的*频率*。

## [课前测验](https://ff-quizzes.netlify.app/en/ml/)

让我们探索文本处理中常用的技术。结合机器学习，这些技术可以帮助您高效地分析大量文本。然而，在将机器学习应用于这些任务之前，让我们先了解NLP专家会遇到的问题。

## NLP常见任务

有不同方法可以分析您正在处理的文本。您可以执行一些任务，通过这些任务能够评估对文本的理解并得出结论。通常，您会按顺序执行这些任务。

### 分词

大多数NLP算法要做的第一件事可能就是将文本拆分为标记或单词。虽然这听起来很简单，但需要考虑标点符号和不同语言的词句分隔符，这可能会变得棘手。您可能需要使用各种方法来确定分割点。

![tokenization](images/tokenization.png)
> 对《傲慢与偏见》中的一个句子进行分词。信息图由[Jen Looper](https://twitter.com/jenlooper)制作

### 词嵌入

[词嵌入](https://wikipedia.org/wiki/Word_embedding)是一种将文本数据转换为数值表示的方法。嵌入的方式使得具有相似含义或一起使用的词会聚集在一起。

![word embeddings](images/embedding.png)
> "我对您的神经非常尊重，它们是我的老朋友。"——《傲慢与偏见》句子的词嵌入。信息图由[Jen Looper](https://twitter.com/jenlooper)制作

✅ 尝试[这个有趣的工具](https://projector.tensorflow.org/)来实验词嵌入。点击一个词会显示相似词的聚类：'toy'与'disney'、'lego'、'playstation'和'console'聚在一起。

### 解析与词性标注

每个经过分词的单词都可以被标记为词性——名词、动词或形容词。句子`the quick red fox jumped over the lazy brown dog`可能会被词性标注为fox=名词，jumped=动词。

![parsing](images/parse.png)

> 解析《傲慢与偏见》中的一个句子。信息图由[Jen Looper](https://twitter.com/jenlooper)制作

解析是识别句子中哪些词相互关联的过程——例如`the quick red fox jumped`是一个形容词-名词-动词序列，与`lazy brown dog`序列分开。

### 词与短语频率

分析大量文本时，一个有用的过程是建立一个包含每个感兴趣的词或短语及其出现频率的字典。短语`the quick red fox jumped over the lazy brown dog`中`the`的词频为2。

让我们看一个统计词频的示例文本。鲁德亚德·吉卜林的诗歌《胜利者》包含以下诗节：

```output
What the moral? Who rides may read.
When the night is thick and the tracks are blind
A friend at a pinch is a friend, indeed,
But a fool to wait for the laggard behind.
Down to Gehenna or up to the Throne,
He travels the fastest who travels alone.
```

由于短语频率可以根据需要不区分大小写或区分大小写，短语`a friend`的频率为2，`the`的频率为6，`travels`的频率为2。

### N-grams

文本可以分割为固定长度的词序列：单个词（unigram）、两个词（bigram）、三个词（trigram）或任意数量的词（n-gram）。

例如，将`the quick red fox jumped over the lazy brown dog`按n-gram值为2处理，会产生以下n-gram：

1. the quick 
2. quick red 
3. red fox
4. fox jumped 
5. jumped over 
6. over the 
7. the lazy 
8. lazy brown 
9. brown dog

将其可视化为在句子上滑动的框可能更容易理解。这是3词n-gram的情况，每句中粗体部分为n-gram：

1.   <u>**the quick red**</u> fox jumped over the lazy brown dog
2.   the **<u>quick red fox</u>** jumped over the lazy brown dog
3.   the quick **<u>red fox jumped</u>** over the lazy brown dog
4.   the quick red **<u>fox jumped over</u>** over the lazy brown dog
5.   the quick red fox **<u>jumped over the</u>** lazy brown dog
6.   the quick red fox jumped **<u>over the lazy</u>** brown dog
7.   the quick red fox jumped over <u>**the lazy brown**</u> dog
8.   the quick red fox jumped over the **<u>lazy brown dog</u>**

![n-grams sliding window](images/n-grams.gif)

> N-gram值为3：信息图由[Jen Looper](https://twitter.com/jenlooper)制作

### 名词短语提取

在大多数句子中，有一个名词是句子的主语或宾语。在英语中，通常可以通过其前面的'a'、'an'或'the'来识别。当NLP任务尝试理解句子含义时，通过"提取名词短语"来识别句子的主语或宾语是一项常见任务。

✅ 在句子"I cannot fix on the hour, or the spot, or the look or the words, which laid the foundation. It is too long ago. I was in the middle before I knew that I had begun."中，您能识别出名词短语吗？

在句子`the quick red fox jumped over the lazy brown dog`中有2个名词短语：**quick red fox**和**lazy brown dog**。

### 情感分析

可以分析句子或文本的情感，即它有多*积极*或多*消极*。情感通过*极性*和*客观性/主观性*来测量。极性从-1.0到1.0（从负到正），客观性从0.0到1.0（最客观到最主观）。

✅ 稍后您将学习使用机器学习确定情感的不同方法，但一种方法是使用由人类专家分类为积极或消极的单词和短语列表，并将该模型应用于文本来计算极性得分。您能看出这在某些情况下如何有效，而在其他情况下效果较差吗？

### 词形变化

词形变化使您能够获取一个单词并得到该单词的单数或复数形式。

### 词形还原

*词元*是一组单词的根词或中心词，例如*flew*、*flies*、*flying*的词元是动词*fly*。

还有对NLP研究者有用的数据库，最著名的是：

### WordNet

[WordNet](https://wordnet.princeton.edu/)是一个单词数据库，包含许多不同语言中每个单词的同义词、反义词和许多其他详细信息。在尝试构建翻译、拼写检查器或任何类型的语言工具时，它非常有用。

## NLP库

幸运的是，您不必自己构建所有这些技术，因为存在优秀的Python库，使非自然语言处理或机器学习专业的开发人员更容易使用。接下来的课程包含更多这些示例，但在这里您将学习一些有用的示例，以帮助您完成下一个任务。

### 练习 - 使用`TextBlob`库

让我们使用一个名为TextBlob的库，因为它包含了处理这类任务的有用API。TextBlob"站在[NLTK](https://nltk.org)和[pattern](https://github.com/clips/pattern)巨人的肩膀上，并与两者配合良好。"它的API中嵌入了大量的机器学习功能。

> 注意：TextBlob有一个有用的[快速入门](https://textblob.readthedocs.io/en/dev/quickstart.html#quickstart)指南，推荐有经验的Python开发者使用

在尝试识别*名词短语*时，TextBlob提供了几种提取器来查找名词短语。

1. 查看`ConllExtractor`。

    ```python
    from textblob import TextBlob
    from textblob.np_extractors import ConllExtractor
    # 导入并创建稍后使用的Conll提取器
    extractor = ConllExtractor()
    
    # 稍后当您需要名词短语提取器时：
    user_input = input("> ")
    user_input_blob = TextBlob(user_input, np_extractor=extractor)  # 注意指定了非默认提取器
    np = user_input_blob.noun_phrases                                    
    ```

    > 这里发生了什么？[ConllExtractor](https://textblob.readthedocs.io/en/dev/api_reference.html?highlight=Conll#textblob.en.np_extractors.ConllExtractor)是"一个使用经过ConLL-2000训练语料库训练的分块解析的名词短语提取器。"ConLL-2000指的是2000年计算自然语言学习会议。每年该会议都会举办一个研讨会来解决棘手的NLP问题，2000年是名词分块。一个模型在《华尔街日报》上训练，"第15-18节作为训练数据（211727个标记），第20节作为测试数据（47377个标记）"。您可以查看使用的程序[这里](https://www.clips.uantwerpen.be/conll2000/chunking/)和[结果](https://ifarm.nl/erikt/research/np-chunking.html)。

### 挑战 - 使用NLP改进您的聊天机器人

在上节课中，您构建了一个非常简单的问答机器人。现在，您将通过分析输入的情感并打印匹配情感的响应，使Marvin更有同情心。您还需要识别`noun_phrase`并就此提问。

构建更好的对话机器人时的步骤：

1. 打印指示，告知用户如何与机器人交互
2. 开始循环
   1. 接受用户输入
   2. 如果用户要求退出，则退出
   3. 处理用户输入并确定适当的情感响应
   4. 如果在情感中检测到名词短语，将其复数化并就该主题请求更多输入
   5. 打印响应
3. 循环回到第2步

以下是使用TextBlob确定情感的代码片段。注意只有四种情感响应*梯度*（如果您愿意，可以有更多）：

```python
if user_input_blob.polarity <= -0.5:
  response = "Oh dear, that sounds bad. "
elif user_input_blob.polarity <= 0:
  response = "Hmm, that's not great. "
elif user_input_blob.polarity <= 0.5:
  response = "Well, that sounds positive. "
elif user_input_blob.polarity <= 1:
  response = "Wow, that sounds great. "
```

以下是一些示例输出来指导您（用户输入以>开头）：

```output
Hello, I am Marvin, the friendly robot.
You can end this conversation at any time by typing 'bye'
After typing each answer, press 'enter'
How are you today?
> I am ok
Well, that sounds positive. Can you tell me more?
> I went for a walk and saw a lovely cat
Well, that sounds positive. Can you tell me more about lovely cats?
> cats are the best. But I also have a cool dog
Wow, that sounds great. Can you tell me more about cool dogs?
> I have an old hounddog but he is sick
Hmm, that's not great. Can you tell me more about old hounddogs?
> bye
It was nice talking to you, goodbye!
```

任务的一个可能解决方案在[这里](https://github.com/microsoft/ML-For-Beginners/blob/main/6-NLP/2-Tasks/solution/bot.py)

✅ 知识检查

1. 您认为这种富有同情心的响应会"欺骗"某人认为机器人真的理解了他们吗？
2. 识别名词短语是否使机器人更"可信"？
3. 为什么从句子中提取"名词短语"是一件有用的事情？

---

实现前面知识检查中的机器人，并在朋友身上测试它。它能欺骗他们吗？您能让您的机器人更"可信"吗？

## 🚀挑战

在前面的知识检查中选择一个任务并尝试实现它。在朋友身上测试机器人。它能欺骗他们吗？您能让您的机器人更"可信"吗？

## [课后测验](https://ff-quizzes.netlify.app/en/ml/)

## 复习与自学

在接下来的几节课中，您将学习更多关于情感分析的知识。在如[KDNuggets](https://www.kdnuggets.com/tag/nlp)上的文章中研究这项有趣的技术。

## 作业

[让机器人回应](assignment.md)
