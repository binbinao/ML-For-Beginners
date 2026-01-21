# 使用机器学习进行翻译和情感分析

在前面的课程中，您学习了如何使用`TextBlob`构建一个基本的聊天机器人，`TextBlob`是一个在幕后使用机器学习来执行基本NLP任务（如名词短语提取）的库。计算语言学的另一个重要挑战是准确地将句子从一种口语或书面语言_翻译_为另一种语言。

## [课前测验](https://ff-quizzes.netlify.app/en/ml/)

翻译是一个非常困难的问题，因为世界上有数千种语言，每种语言都有非常不同的语法规则。一种方法是将一种语言（例如英语）的形式语法规则转换为非语言依赖的结构，然后通过转换回另一种语言进行翻译。这种方法意味着您需要采取以下步骤：

1. **识别**。将输入语言中的单词识别或标记为名词、动词等。
2. **创建翻译**。生成目标语言格式中每个单词的直接翻译。

### 示例句子，英语到爱尔兰语

在"英语"中，句子_I feel happy_是三个词的顺序：

- **主语** (I)
- **动词** (feel)
- **形容词** (happy)

然而，在"爱尔兰语"中，同一个句子具有非常不同的语法结构——像"*happy*"或"*sad*"这样的情绪被表达为_在你身上_。

英语短语`I feel happy`在爱尔兰语中会是`Tá athas orm`。*字面*翻译会是`Happy is upon me`。

说爱尔兰语的人翻译成英语时会说`I feel happy`，而不是`Happy is upon me`，因为他们理解句子的意思，即使单词和句子结构不同。

爱尔兰语句子的正式顺序是：

- **动词** (Tá or is)
- **形容词** (athas, or happy)
- **主语** (orm, or upon me)

## 翻译

一个天真的翻译程序可能只会翻译单词，而忽略句子结构。

✅ 如果您在成年后学习了第二（或第三、第四等）语言，您可能一开始会用母语思考，然后在脑海中逐词将概念翻译成第二语言，最后说出您的翻译。这与天真的计算机翻译程序所做的类似。要获得流利度，超越这个阶段非常重要！

天真的翻译会导致糟糕的（有时是滑稽的）误译：`I feel happy`在爱尔兰语中字面翻译为`Mise bhraitheann athas`。这（字面上）意味着`me feel happy`，并不是一个有效的爱尔兰语句子。尽管英语和爱尔兰语是相邻两个岛上使用的语言，但它们是具有不同语法结构的非常不同的语言。

> 您可以观看一些关于爱尔兰语言传统的视频，例如[这个](https://www.youtube.com/watch?v=mRIaLSdRMMs)

### 机器学习方法

到目前为止，您已经了解了自然语言处理的形式规则方法。另一种方法是忽略单词的含义，而是_使用机器学习来检测模式_。如果您有大量文本（*语料库*）或两种语言（源语言和目标语言）的文本（*语料库*），这可以在翻译中发挥作用。

例如，考虑*傲慢与偏见*的案例，这是简·奥斯汀在1813年写的一部著名的英语小说。如果您查阅这本书的英文版和法文版的人工翻译，您可以在一种语言中检测到_惯用地_翻译成另一种语言的短语。您将在一分钟内完成这个操作。

例如，当英语短语`I have no money`字面翻译成法语时，可能会变成`Je n'ai pas de monnaie`。"Monnaie"是一个棘手的法语'假同源词'，因为'money'和'monnaie'不是同义词。人工可能会做出的更好翻译是`Je n'ai pas d'argent`，因为它更好地传达了您没有钱的意思（而不是'零钱'，这是'monnaie'的含义）。

![monnaie](images/monnaie.png)

> 图片由[Jen Looper](https://twitter.com/jenlooper)制作

如果机器学习模型有足够的人工翻译来构建模型，它可以通过识别之前由两种语言的专家人类翻译的文本中的常见模式来提高翻译的准确性。

### 练习 - 翻译

您可以使用`TextBlob`翻译句子。尝试**傲慢与偏见**著名的第一行：

```python
from textblob import TextBlob

blob = TextBlob(
    "It is a truth universally acknowledged, that a single man in possession of a good fortune, must be in want of a wife!"
)
print(blob.translate(to="fr"))

```

`TextBlob`在翻译方面做得相当好："C'est une vérité universellement reconnue, qu'un homme célibataire en possession d'une bonne fortune doit avoir besoin d'une femme!"。 

可以认为，TextBlob的翻译实际上比V. Leconte和Ch. Pressoir在1932年的法语译本更为准确：

"C'est une vérité universelle qu'un célibataire pourvu d'une belle fortune doit avoir envie de se marier, et, si peu que l'on sache de son sentiment à cet egard, lorsqu'il arrive dans une nouvelle résidence, cette idée est si bien fixée dans l'esprit de ses voisins qu'ils le considèrent sur-le-champ comme la propriété légitime de l'une ou l'autre de leurs filles."

在这种情况下，由机器学习指导的翻译比人类翻译者做得更好，后者不必要地为了'清晰度'而将单词放回原作者的口中。

> 这里发生了什么？为什么TextBlob如此擅长翻译？嗯，在幕后，它使用的是谷歌翻译，这是一个复杂的人工智能，能够解析数百万个短语，以预测手头任务的最佳字符串。这里没有任何人工操作，您需要互联网连接才能使用`blob.translate`。

✅ 尝试更多句子。机器学习还是人工翻译哪个更好？在哪些情况下？

## 情感分析

机器学习可以发挥非常好作用的另一个领域是情感分析。非机器学习的情感分析方法是识别'积极'和'消极'的单词和短语。然后，给定一段新文本，计算积极、消极和中性单词的总值，以识别整体情感。

这种方法很容易被愚弄，就像您在Marvin任务中可能看到的那样——句子`Great, that was a wonderful waste of time, I'm glad we are lost on this dark road`是一个讽刺的、消极情感的句子，但简单的算法将'great'、'wonderful'、'glad'检测为积极，将'waste'、'lost'和'dark'检测为消极。整体情感被这些矛盾的单词所左右。

✅ 停一下，想想我们作为人类说话者如何传达讽刺。语调变化起着重要作用。尝试用不同的方式说"Well, that film was awesome"，看看您的声音如何传达意义。

### 机器学习方法

机器学习方法将是手动收集消极和积极的文本主体——推文、电影评论或人类给出评分_和_书面意见的任何内容。然后可以应用NLP技术来分析意见和评分，从而出现模式（例如，积极的电影评论往往比消极的电影评论更频繁地出现短语'Oscar worthy'，或者积极的餐厅评论说'gourmet'的次数远远超过'disgusting'）。

> ⚖️ **示例**：如果您在一位政治家的办公室工作，并且有一项新法律正在辩论中，选民可能会写信给办公室，发送支持或反对这项新法律的电子邮件。假设您被指派阅读这些电子邮件并将它们分类到两个堆中，*支持*和*反对*。如果有很多电子邮件，您可能会因为尝试阅读所有邮件而不堪重负。如果一个机器人能为您阅读所有邮件，理解它们并告诉您每封邮件属于哪个堆，那不是很好吗？
> 
> 实现这一点的一种方法是使用机器学习。您将用一部分*反对*邮件和一部分*支持*邮件来训练模型。模型将倾向于将短语和单词与反对方和支持方联系起来，但*它不会理解任何内容*，只会知道某些单词和模式更可能出现在*反对*或*支持*邮件中。您可以用一些未用于训练模型的邮件进行测试，看看它是否得出与您相同的结论。然后，一旦您对模型的准确性感到满意，您就可以处理未来的邮件，而无需阅读每一封。

✅ 这个过程听起来像您在之前的课程中使用过的过程吗？

## 练习 - 情感句子

情感通过*-1到1的极性*来衡量，意味着-1是最消极的情感，1是最积极的情感。情感还通过0-1的分数来衡量的客观性（0）和主观性（1）。

再看一下简·奥斯汀的*傲慢与偏见*。文本可在[Project Gutenberg](https://www.gutenberg.org/files/1342/1342-h/1342-h.htm)获得。下面的示例展示了一个简短的程序，它分析书中第一句和最后一句的情感，并显示其情感极性和主观性/客观性分数。

您应该使用`TextBlob`库（如上所述）来确定以下任务中的`sentiment`（您不必编写自己的情感计算器）。

```python
from textblob import TextBlob

quote1 = """It is a truth universally acknowledged, that a single man in possession of a good fortune, must be in want of a wife."""

quote2 = """Darcy, as well as Elizabeth, really loved them; and they were both ever sensible of the warmest gratitude towards the persons who, by bringing her into Derbyshire, had been the means of uniting them."""

sentiment1 = TextBlob(quote1).sentiment
sentiment2 = TextBlob(quote2).sentiment

print(quote1 + " has a sentiment of " + str(sentiment1))
print(quote2 + " has a sentiment of " + str(sentiment2))
```

您会看到以下输出：

```output
It is a truth universally acknowledged, that a single man in possession of a good fortune, must be in want # of a wife. has a sentiment of Sentiment(polarity=0.20952380952380953, subjectivity=0.27142857142857146)

Darcy, as well as Elizabeth, really loved them; and they were
     both ever sensible of the warmest gratitude towards the persons
      who, by bringing her into Derbyshire, had been the means of
      uniting them. has a sentiment of Sentiment(polarity=0.7, subjectivity=0.8)
```

## 挑战 - 检查情感极性

您的任务是使用情感极性来确定*傲慢与偏见*中绝对积极的句子是否比绝对消极的句子多。对于这个任务，您可以假设极性分数为1或-1分别代表绝对积极或绝对消极。

**步骤：**

1. 从Project Gutenberg下载[傲慢与偏见的副本](https://www.gutenberg.org/files/1342/1342-h/1342-h.htm)作为.txt文件。删除文件开头和结尾的元数据，只保留原始文本
2. 在Python中打开文件并将内容提取为字符串
3. 使用书籍字符串创建TextBlob
4. 在循环中分析书中的每个句子
   1. 如果极性为1或-1，将句子存储在积极或消极消息的数组或列表中
5. 最后，分别打印出所有积极句子和消极句子以及每种的数量。

这是一个示例[解决方案](https://github.com/microsoft/ML-For-Beginners/blob/main/6-NLP/3-Translation-Sentiment/solution/notebook.ipynb)。

✅ 知识检查

1. 情感基于句子中使用的单词，但代码是否*理解*这些单词？
2. 您认为情感极性准确吗？换句话说，您*同意*这些分数吗？
   1. 特别是，您同意还是不同意以下句子的绝对**积极**极性？
      * “What an excellent father you have, girls!” said she, when the door was shut.
      * “Your examination of Mr. Darcy is over, I presume,” said Miss Bingley; “and pray what is the result?” “I am perfectly convinced by it that Mr. Darcy has no defect.
      * How wonderfully these sort of things occur!
      * I have the greatest dislike in the world to that sort of thing.
      * Charlotte is an excellent manager, I dare say.
      * “This is delightful indeed!
      * I am so happy!
      * Your idea of the ponies is delightful.
   2. 接下来的3个句子被评为绝对积极情感，但仔细阅读后，它们不是积极的句子。为什么情感分析认为它们是积极的句子？
      * Happy shall I be, when his stay at Netherfield is over!” “I wish I could say anything to comfort you,” replied Elizabeth; “but it is wholly out of my power.
      * If I could but see you as happy!
      * Our distress, my dear Lizzy, is very great.
   3. 您同意还是不同意以下句子的绝对**消极**极性？
      - Everybody is disgusted with his pride.
      - “I should like to know how he behaves among strangers.” “You shall hear then—but prepare yourself for something very dreadful.
      - The pause was to Elizabeth’s feelings dreadful.
      - It would be dreadful!

✅ 任何简·奥斯汀的爱好者都会理解，她经常用她的书来批判英国摄政时期社会中更荒谬的方面。*傲慢与偏见*的主角伊丽莎白·贝内特是一个敏锐的社会观察者（像作者一样），她的语言通常非常细微。甚至达西先生（故事中的爱情对象）也注意到伊丽莎白俏皮和戏谑的语言使用："I have had the pleasure of your acquaintance long enough to know that you find great enjoyment in occasionally professing opinions which in fact are not your own."

---

## 🚀挑战

您能否通过从用户输入中提取其他特征来使Marvin变得更好？

## [课后测验](https://ff-quizzes.netlify.app/en/ml/)

## 复习与自学

从文本中提取情感的方法有很多。想想可能利用这种技术的商业应用。想想它如何会出错。阅读更多关于分析情感的企业级系统，如[Azure Text Analysis](https://docs.microsoft.com/azure/cognitive-services/Text-Analytics/how-tos/text-analytics-how-to-sentiment-analysis?tabs=version-3-1?WT.mc_id=academic-77952-leestott)。测试上面的一些傲慢与偏见句子，看看它是否能检测到细微差别。

## 作业

[诗意的许可](assignment.md)
