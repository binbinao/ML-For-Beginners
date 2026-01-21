# 使用 Python 和 Scikit-learn 构建回归模型入门

![回归模型要点图解](../../sketchnotes/ml-regression.png)

> 插图作者：[Tomomi Imura](https://www.twitter.com/girlie_mac)

## [课前测验](https://ff-quizzes.netlify.app/en/ml/)

> ### [本课程也有 R 语言版本！](./solution/R/lesson_1.html)

## 简介

在这四节课中，你将学习如何构建回归模型。我们很快就会讨论这些模型的用途。但在开始之前，请确保你已经配置好了正确的工具来开始这个过程！

在本节课中，你将学习如何：

- 为本地机器学习任务配置你的计算机。
- 使用 Jupyter notebooks。
- 使用 Scikit-learn，包括安装过程。
- 通过动手练习探索线性回归。

## 安装和配置

[![机器学习入门 - 配置工具以构建机器学习模型](https://img.youtube.com/vi/-DfeD2k2Kj0/0.jpg)](https://youtu.be/-DfeD2k2Kj0 "机器学习入门 -配置工具以构建机器学习模型")

> 🎥 点击上方图片观看关于配置计算机进行机器学习的短视频。

1. **安装 Python**。确保你的计算机上已安装 [Python](https://www.python.org/downloads/)。你将使用 Python 进行许多数据科学和机器学习任务。大多数计算机系统已经包含了 Python 安装。此外，还有一些有用的 [Python 编程包](https://code.visualstudio.com/learn/educators/installers?WT.mc_id=academic-77952-leestott) 可用，可以简化某些用户的设置。

   然而，Python 的某些用法需要一个版本的软件，而其他的则需要不同的版本。因此，在 [虚拟环境](https://docs.python.org/3/library/venv.html) 中工作非常有用。

2. **安装 Visual Studio Code**。确保你的计算机上安装了 Visual Studio Code。按照这些说明进行 [安装 Visual Studio Code](https://code.visualstudio.com/) 的基本安装。在本课程中，你将在 Visual Studio Code 中使用 Python，所以你可能需要复习如何 [配置 Visual Studio Code](https://docs.microsoft.com/learn/modules/python-install-vscode?WT.mc_id=academic-77952-leestott) 进行 Python 开发。

   > 通过完成这个 [学习模块集合](https://docs.microsoft.com/users/jenlooper-2911/collections/mp1pagggd5qrq7?WT.mc_id=academic-77952-leestott) 来熟悉 Python
   >
   > [![使用 Visual Studio Code 设置 Python](https://img.youtube.com/vi/yyQM70vi7V8/0.jpg)](https://youtu.be/yyQM70vi7V8 "使用 Visual Studio Code 设置 Python")
   >
   > 🎥 点击上方图片观看视频：在 VS Code 中使用 Python。

3. **安装 Scikit-learn**，按照 [这些说明](https://scikit-learn.org/stable/install.html) 进行。由于你需要确保使用 Python 3，建议使用虚拟环境。注意，如果你在 M1 Mac 上安装这个库，上面链接的页面有特别说明。

4. **安装 Jupyter Notebook**。你需要 [安装 Jupyter 包](https://pypi.org/project/jupyter/)。

## 你的机器学习开发环境

你将使用 **notebooks（笔记本）** 来开发 Python 代码并创建机器学习模型。这种文件类型是数据科学家的常用工具，可以通过它们的后缀或扩展名 `.ipynb` 来识别。

Notebooks 是一个交互式环境，允许开发者编写代码，并在代码周围添加注释和编写文档，这对于实验性或研究导向的项目非常有帮助。

[![机器学习入门 - 设置 Jupyter Notebooks 以开始构建回归模型](https://img.youtube.com/vi/7E-jC8FLA2E/0.jpg)](https://youtu.be/7E-jC8FLA2E "机器学习入门 - 设置 Jupyter Notebooks 以开始构建回归模型")

> 🎥 点击上方图片观看关于完成此练习的短视频。

### 练习 - 使用 notebook

在这个文件夹中，你会发现文件 _notebook.ipynb_。

1. 在 Visual Studio Code 中打开 _notebook.ipynb_。

   Jupyter 服务器将启动，并运行 Python 3+。你会发现 notebook 中有一些可以 `运行` 的区域，即代码块。你可以通过选择看起来像播放按钮的图标来运行代码块。

2. 选择 `md` 图标并添加一些 markdown，以及以下文本 **# 欢迎使用你的 notebook**。

   接下来，添加一些 Python 代码。

3. 在代码块中输入 **print('hello notebook')**。
4. 选择箭头运行代码。

   你应该看到打印的语句：

    ```output
    hello notebook
    ```

![VS Code 打开 notebook 的界面](images/notebook.jpg)

你可以在代码中穿插注释来自我记录 notebook。

✅ 想一想，Web 开发者的工作环境与数据科学家的工作环境有何不同。

## 开始使用 Scikit-learn

现在 Python 已经在你的本地环境中设置好，并且你已经熟悉了 Jupyter notebooks，让我们同样熟悉 Scikit-learn（发音为 `sci`，如 `science`）。Scikit-learn 提供了[广泛的 API](https://scikit-learn.org/stable/modules/classes.html#api-ref) 来帮助你执行机器学习任务。

根据它们的[网站](https://scikit-learn.org/stable/getting_started.html)，"Scikit-learn 是一个开源机器学习库，支持监督学习和无监督学习。它还提供各种模型拟合、数据预处理、模型选择和评估的工具，以及许多其他实用程序。"

在本课程中，你将使用 Scikit-learn 和其他工具来构建机器学习模型，以执行我们所谓的"传统机器学习"任务。我们有意识地避免了神经网络和深度学习，因为它们会在我们即将推出的"人工智能入门"课程中更好地涵盖。

Scikit-learn 使构建模型和评估其使用变得简单。它主要专注于使用数值数据，并包含几个现成的数据集作为学习工具。它还包括预构建的模型供学生试用。让我们先探索加载预打包数据和使用内置估计器的过程，使用 Scikit-learn 和一些基本数据构建你的第一个机器学习模型。

## 练习 - 你的第一个 Scikit-learn notebook

> 本教程受 Scikit-learn 网站上的[线性回归示例](https://scikit-learn.org/stable/auto_examples/linear_model/plot_ols.html#sphx-glr-auto-examples-linear-model-plot-ols-py)启发。

[![机器学习入门 - Python 中的第一个线性回归项目](https://img.youtube.com/vi/2xkXL5EUpS0/0.jpg)](https://youtu.be/2xkXL5EUpS0 "机器学习入门 - Python 中的第一个线性回归项目")

> 🎥 点击上方图片观看关于完成此练习的短视频。

在与本课程相关的 _notebook.ipynb_ 文件中，通过点击"垃圾桶"图标清除所有单元格。

在本节中，你将处理 Scikit-learn 中内置的关于糖尿病的小数据集，用于学习目的。想象你想测试针对糖尿病患者的治疗方法。机器学习模型可能有助于你根据变量组合确定哪些患者会对治疗反应更好。即使是基本的回归模型，当可视化时，也可能显示关于变量的信息，帮助你组织理论临床试验。

✅ 有许多类型的回归方法，你选择哪一种取决于你寻找的答案。如果你想预测给定年龄的人的可能身高，你会使用线性回归，因为你寻求一个**数值**。如果你有兴趣确定某种类型的菜系是否应该被认为是素食的，你在寻找一个**类别分配**，所以你会使用逻辑回归。你稍后会学到更多关于逻辑回归的知识。想想一些你可以向数据提出的问题，以及其中哪些方法会更合适。

让我们开始这个任务。

### 导入库

对于这个任务，我们将导入一些库：

- **matplotlib**。它是一个有用的[绘图工具](https://matplotlib.org/)，我们将用它来创建线图。
- **numpy**。[numpy](https://numpy.org/doc/stable/user/whatisnumpy.html) 是一个有用的库，用于在 Python 中处理数值数据。
- **sklearn**。这是 [Scikit-learn](https://scikit-learn.org/stable/user_guide.html) 库。

导入一些库来帮助你完成任务。

1. 通过输入以下代码添加导入：

   ```python
   import matplotlib.pyplot as plt
   import numpy as np
   from sklearn import datasets, linear_model, model_selection
   ```

   上面你正在导入 `matplotlib`、`numpy`，并且你正在从 `sklearn` 导入 `datasets`、`linear_model` 和 `model_selection`。`model_selection` 用于将数据分割为训练集和测试集。

### 糖尿病数据集

内置的[糖尿病数据集](https://scikit-learn.org/stable/datasets/toy_dataset.html#diabetes-dataset)包括 442 个关于糖尿病的数据样本，有 10 个特征变量，其中一些包括：

- age：年龄（年）
- bmi：体重指数
- bp：平均血压
- s1 tc：T 细胞（一种白细胞）

✅ 该数据集包括"性别"作为一个特征变量，这对糖尿病研究很重要。许多医学数据集包括这种类型的二分类。想想这样的分类可能会如何将某些人群排除在治疗之外。

现在，加载 X 和 y 数据。

> 🎓 记住，这是监督学习，我们需要一个名为 'y' 的目标。

在一个新的代码单元格中，通过调用 `load_diabetes()` 加载糖尿病数据集。输入 `return_X_y=True` 表示 `X` 将是数据矩阵，`y` 将是回归目标。

1. 添加一些打印命令来显示数据矩阵的形状及其第一个元素：

    ```python
    X, y = datasets.load_diabetes(return_X_y=True)
    print(X.shape)
    print(X[0])
    ```

    你作为响应得到的是一个元组。你正在做的是将元组的两个前一个值分别分配给 `X` 和 `y`。了解更多[关于元组](https://wikipedia.org/wiki/Tuple)。

    你可以看到这个数据有 442 个项目，形状为 10 个元素的数组：

    ```text
    (442, 10)
    [ 0.03807591  0.05068012  0.06169621  0.02187235 -0.0442235  -0.03482076
    -0.04340085 -0.00259226  0.01990842 -0.01764613]
    ```

    ✅ 思考一下数据和回归目标之间的关系。线性回归预测特征 X 和目标变量 y 之间的关系。你能在文档中找到糖尿病数据集的[目标](https://scikit-learn.org/stable/datasets/toy_dataset.html#diabetes-dataset)吗？考虑到这个目标，这个数据集展示了什么？

2. 接下来，选择此数据集的一部分进行绘制，通过选择数据集的第 3 列。你可以使用 `:` 运算符选择所有行，然后使用索引（2）选择第 3 列。你还可以使用 `reshape(n_rows, n_columns)` 将数据重塑为二维数组 - 绘图所需要。如果其中一个参数是 -1，相应的维度会自动计算。

   ```python
   X = X[:, 2]
   X = X.reshape((-1,1))
   ```

   ✅ 随时打印出数据以检查其形状。

3. 现在你已经准备好要绘制的数据，你可以看看机器是否可以帮助确定这个数据集中数字之间的逻辑分割。为此，你需要将数据（X）和目标（y）都分割为测试集和训练集。Scikit-learn 有一个简单的方法来做到这一点；你可以在给定点分割你的测试数据。

   ```python
   X_train, X_test, y_train, y_test = model_selection.train_test_split(X, y, test_size=0.33)
   ```

4. 现在你准备好训练你的模型了！加载线性回归模型并使用你的 X 和 y 训练集通过 `model.fit()` 训练它：

    ```python
    model = linear_model.LinearRegression()
    model.fit(X_train, y_train)
    ```

    ✅ `model.fit()` 是你将在许多机器学习库（如 TensorFlow）中看到的函数

5. 然后，使用测试数据创建预测，使用函数 `predict()`。这将用于在模型的数据分组之间画一条线

    ```python
    y_pred = model.predict(X_test)
    ```

6. 现在是在图表中显示数据的时候了。Matplotlib 是一个非常有用的工具。创建所有 X 和 y 测试数据的散点图，并使用预测在最合适的地方画一条线，在模型的数据分组之间。

    ```python
    plt.scatter(X_test, y_test,  color='black')
    plt.plot(X_test, y_pred, color='blue', linewidth=3)
    plt.xlabel('标准化 BMI')
    plt.ylabel('疾病进展')
    plt.title('显示糖尿病进展与BMI关系的图表')
    plt.show()
    ```

   ![显示糖尿病数据点的散点图](./images/scatterplot.png)

   ✅ 想想这里发生了什么。一条直线穿过许多小数据点，但它到底在做什么？你能看到你应该能够如何使用这条线来预测一个新的、未见过的数据点应该相对于图的 y 轴适合在哪里吗？试着用言语描述这个模型的实际用途。

恭喜，你构建了你的第一个线性回归模型，用它创建了预测，并在图表中显示了它！

---

## 🚀挑战

绘制此数据集中的不同变量。提示：编辑这一行：`X = X[:,2]`。考虑到这个数据集的目标，你能发现关于糖尿病作为一种疾病的进展的什么信息？

## [课后测验](https://ff-quizzes.netlify.app/en/ml/)

## 复习与自学

在本教程中，你使用了简单线性回归，而不是单变量或多元线性回归。阅读一点关于这些方法之间的差异，或者看看[这个视频](https://www.coursera.org/lecture/quantifying-relationships-regression-models/linear-vs-nonlinear-categorical-variables-ai2Ef)

阅读更多关于回归概念的内容，并思考可以用这种技术回答什么类型的问题。参加这个[教程](https://docs.microsoft.com/learn/modules/train-evaluate-regression-models?WT.mc_id=academic-77952-leestott)来加深你的理解。

## 作业

[不同的数据集](assignment.md)
