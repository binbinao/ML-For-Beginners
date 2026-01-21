# 使用 Scikit-learn 构建回归模型：准备和可视化数据

![数据可视化信息图](./images/data-visualization.png)

信息图作者：[Dasani Madipalli](https://twitter.com/dasani_decoded)

## [课前测验](https://ff-quizzes.netlify.app/en/ml/)

> ### [本课程也有 R 语言版本！](./solution/R/lesson_2.html)

## 简介

既然你已经配置好了开始使用 Scikit-learn 构建机器学习模型所需的工具，那么你现在就可以开始向数据提问了。在处理数据并应用机器学习解决方案时，理解如何提出正确的问题以正确释放数据集的潜力是非常重要的。

在本节课中，你将学习：

- 如何为模型构建准备你的数据。
- 如何使用 Matplotlib 进行数据可视化。

## 向你的数据提出正确的问题

你需要回答的问题将决定你将利用哪种类型的机器学习算法。而你得到的答案的质量在很大程度上取决于数据的性质。

看看本课程提供的[数据](https://github.com/microsoft/ML-For-Beginners/blob/main/2-Regression/data/US-pumpkins.csv)。你可以在 VS Code 中打开这个 .csv 文件。快速浏览一下就会发现，其中存在空白，混合了字符串和数值数据。还有一个奇怪的列叫做'Package'（包装），其中的数据是'sacks'（袋子）、'bins'（箱子）和其他值的混合。事实上，这个数据有点混乱。

[![ML for beginners - How to Analyze and Clean a Dataset](https://img.youtube.com/vi/5qGjczWTrDQ/0.jpg)](https://youtu.be/5qGjczWTrDQ "ML for beginners - How to Analyze and Clean a Dataset")

> 🎥 点击上方图片观看关于为本课程准备数据的短视频。

事实上，获得一个完全可以直接用来创建机器学习模型的数据集并不常见。在本节课中，你将学习如何使用标准 Python 库准备原始数据集。你还将学习各种可视化数据的技术。

## 案例研究："南瓜市场"

在这个文件夹中，你会在根目录的 `data` 文件夹中找到一个名为 [US-pumpkins.csv](https://github.com/microsoft/ML-For-Beginners/blob/main/2-Regression/data/US-pumpkins.csv) 的 .csv 文件，其中包含 1757 行关于南瓜市场的数据，按城市分组。这是从美国农业部发布的[ Specialty Crops Terminal Markets Standard Reports](https://www.marketnews.usda.gov/mnp/fv-report-config-step1?type=termPrice) 中提取的原始数据。

### 准备数据

这些数据属于公共领域。可以从美国农业部网站下载许多单独的文件，按城市分类。为了避免太多单独的文件，我们将所有城市的数据合并到一个电子表格中，因此我们其实已经稍微_准备_了一些数据。接下来，让我们仔细看看这些数据。

### 南瓜数据 - 初步结论

你注意到这些数据的哪些特点？你已经看到其中有字符串、数字、空白和一些需要理解的奇怪值的混合。

使用回归技术，你可以对这些数据提出什么问题？"预测给定月份出售的南瓜价格"怎么样。再次查看数据，你需要进行一些更改才能为任务创建必要的数据结构。

## 练习 - 分析南瓜数据

让我们使用 [Pandas](https://pandas.pydata.org/)（名称代表 `Python Data Analysis`），这是一个非常有用的数据整形工具，来分析和准备这个南瓜数据。

### 首先，检查缺失的日期

你首先需要采取措施检查缺失的日期：

1. 将日期转换为月份格式（这些是美国日期，所以格式是 `MM/DD/YYYY`）。
2. 将月份提取到新列中。

在 Visual Studio Code 中打开 _notebook.ipynb_ 文件，并将电子表格导入到新的 Pandas 数据框中。

1. 使用 `head()` 函数查看前五行。

    ```python
    import pandas as pd
    pumpkins = pd.read_csv('../data/US-pumpkins.csv')
    pumpkins.head()
    ```

    ✅ 你会使用什么函数来查看最后五行？

1. 检查当前数据框中是否有缺失数据：

    ```python
    pumpkins.isnull().sum()
    ```

    存在缺失数据，但对于手头的任务可能无关紧要。

1. 为了使你的数据框更易于使用，使用 `loc` 函数只选择你需要的列，该函数从原始数据框中提取一组行（作为第一个参数传递）和列（作为第二个参数传递）。下面的表达式 `:` 表示"所有行"。

    ```python
    columns_to_select = ['Package', 'Low Price', 'High Price', 'Date']
    pumpkins = pumpkins.loc[:, columns_to_select]
    ```

### 其次，确定南瓜的平均价格

思考如何确定给定月份南瓜的平均价格。你会为这个任务选择哪些列？提示：你需要 3 列。

解决方案：取 `Low Price`（最低价）和 `High Price`（最高价）列的平均值来填充新的 Price（价格）列，并将 Date 列转换为仅显示月份。幸运的是，根据上面的检查，日期或价格没有缺失数据。

1. 要计算平均值，添加以下代码：

    ```python
    price = (pumpkins['Low Price'] + pumpkins['High Price']) / 2

    month = pd.DatetimeIndex(pumpkins['Date']).month

    ```

   ✅ 随时可以使用 `print(month)` 打印任何你想检查的数据。

2. 现在，将转换后的数据复制到新的 Pandas 数据框中：

    ```python
    new_pumpkins = pd.DataFrame({'Month': month, 'Package': pumpkins['Package'], 'Low Price': pumpkins['Low Price'],'High Price': pumpkins['High Price'], 'Price': price})
    ```

    打印出你的数据框，你将看到一个干净、整洁的数据集，你可以基于它构建新的回归模型。

### 等等！这里有些奇怪

如果你查看 `Package`（包装）列，南瓜以许多不同的配置出售。有些以 '1 1/9 bushel'（蒲式耳）的度量出售，有些以 '1/2 bushel' 的度量出售，有些按南瓜出售，有些按磅出售，还有一些是不同宽度的大箱子。

> 南瓜似乎很难称重一致

深入研究原始数据，有趣的是，任何 `Unit of Sale`（销售单位）等于 'EACH'（每个）或 'PER BIN'（每箱）的东西也有按英寸、每箱或 'each' 类型的 `Package`。南瓜似乎很难称重一致，所以让我们通过选择 `Package` 列中包含字符串 'bushel' 的南瓜来过滤它们。

1. 在文件顶部、初始 .csv 导入下添加过滤器：

    ```python
    pumpkins = pumpkins[pumpkins['Package'].str.contains('bushel', case=True, regex=True)]
    ```

    如果你现在打印数据，你可以看到你只得到大约 415 行包含按蒲式耳出售的南瓜数据。

### 等等！还有一件事要做

你注意到蒲式耳数量每行都有变化吗？你需要标准化定价，以便显示每蒲式耳的价格，所以做一些数学运算来标准化它。

1. 在创建 new_pumpkins 数据框的块后添加这些行：

    ```python
    new_pumpkins.loc[new_pumpkins['Package'].str.contains('1 1/9'), 'Price'] = price/(1 + 1/9)

    new_pumpkins.loc[new_pumpkins['Package'].str.contains('1/2'), 'Price'] = price/(1/2)
    ```

✅ 根据 [The Spruce Eats](https://www.thespruceeats.com/how-much-is-a-bushel-1389308)，蒲式耳的重量取决于农产品的类型，因为它是体积测量。"例如，一蒲式耳番茄应该重 56 磅……叶菜和绿叶菜占据更多空间但重量更少，所以一蒲式耳菠菜只有 20 磅。"这一切都非常复杂！让我们不要费心进行蒲式耳到磅的转换，而是按蒲式耳定价。然而，所有这些对南瓜蒲式耳的研究都表明了解数据的性质是多么重要！

现在，你可以根据它们的蒲式耳测量分析每单位的定价。如果你再打印一次数据，你可以看到它是如何标准化的。

✅ 你注意到按半蒲式耳出售的南瓜非常贵吗？你能弄清楚为什么吗？提示：小南瓜比大南瓜贵得多，可能是因为一个大的空心南瓜派占据了未使用的空间，所以每蒲式耳有更多的小南瓜。

## 可视化策略

数据科学家的角色的一部分是展示他们正在处理的数据的质量和性质。为此，他们经常创建有趣的可视化，或显示数据不同方面的图表、图形和图表。通过这种方式，他们能够直观地展示否则很难发现的关系和差距。

[![ML for beginners - How to Visualize Data with Matplotlib](https://img.youtube.com/vi/SbUkxH6IJo0/0.jpg)](https://youtu.be/SbUkxH6IJo0 "ML for beginners - How to Visualize Data with Matplotlib")

> 🎥 点击上方图片观看关于为本课程可视化数据的短视频。

可视化还有助于确定最适合数据的技术。例如，似乎跟随一条线的散点图表明数据是线性回归练习的良好候选者。

一个在 Jupyter notebooks 中运行良好的数据可视化库是 [Matplotlib](https://matplotlib.org/)（你在上一节课中也看到了它）。

> 在[这些教程](https://docs.microsoft.com/learn/modules/explore-analyze-data-with-python?WT.mc_id=academic-77952-leestott)中获得更多数据可视化的经验。

## 练习 - 尝试 Matplotlib

尝试创建一些基本图来显示你刚刚创建的新数据框。基本的线图会显示什么？

1. 在文件顶部导入 Matplotlib，在 Pandas 导入下：

    ```python
    import matplotlib.pyplot as plt
    ```

1. 重新运行整个 notebook 以刷新。
1. 在 notebook 底部，添加一个单元格以将数据绘制为框：

    ```python
    price = new_pumpkins.Price
    month = new_pumpkins.Month
    plt.scatter(price, month)
    plt.show()
    ```

    ![显示价格与月份关系的散点图](./images/scatterplot.png)

    这是一个有用的图吗？有什么让你惊讶的地方吗？

    它并不是特别有用，因为它所做的只是在给定月份的数据中显示为点的分布。

### 使它有用

要让图表显示有用的数据，通常需要以某种方式对数据进行分组。让我们尝试创建一个图表，其中 y 轴显示月份，数据展示数据的分布。

1. 添加一个单元格以创建分组条形图：

    ```python
    new_pumpkins.groupby(['Month'])['Price'].mean().plot(kind='bar')
    plt.ylabel("南瓜价格")
    ```

    ![显示价格与月份关系的条形图](./images/barchart.png)

    这是一个更有用的数据可视化！它似乎表明南瓜的最高价格出现在 9 月和 10 月。这符合你的预期吗？为什么或为什么不？

---

## 🚀 挑战

探索 Matplotlib 提供的不同类型的可视化。哪些类型最适合回归问题？

## [课后测验](https://ff-quizzes.netlify.app/en/ml/)

## 复习与自学

看看可视化数据的许多方法。列出可用的各种库，并注意哪些最适合给定类型的任务，例如 2D 可视化与 3D 可视化。你发现了什么？

## 作业

[探索可视化](assignment.md)
