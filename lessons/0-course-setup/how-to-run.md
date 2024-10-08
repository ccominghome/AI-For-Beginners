# 如何运行代码

本课程包含许多可执行的示例和实验，您可能希望运行它们.为了做到这一点，您需要能够在本课程提供的 Jupyter 笔记本中执行 Python 代码.您有几种运行代码的选项：

## 在本地计算机上运行

要在本地计算机上运行代码，您需要安装某个版本的 Python.我个人推荐安装 **[miniconda](https://conda.io/en/latest/miniconda.html)** —— 这是一个相当轻量级的安装程序，支持用于不同 Python **虚拟环境**的 `conda` 包管理器.

安装 miniconda 后，您需要克隆仓库并创建一个用于本课程的虚拟环境：

```bash
git clone http://github.com/microsoft/ai-for-beginners
cd ai-for-beginners
conda env create --name ai4beg --file .devcontainer/environment.yml
conda activate ai4beg
```

### 使用带有 Python 扩展的 Visual Studio Code

使用 [Visual Studio Code](http://code.visualstudio.com/?WT.mc_id=academic-77998-cacaste) 和 [Python 扩展](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-77998-cacaste) 打开课程是最好的方式之一.

> **注意**: 一旦您克隆并在 VS Code 中打开目录，它将自动建议您安装 Python 扩展.您还需要按照上述说明安装 miniconda.

> **注意**: 如果 VS Code 建议您在容器中重新打开仓库，您需要拒绝，以使用本地 Python 安装.

### 在浏览器中使用 Jupyter

您还可以直接在本地计算机的浏览器中使用 Jupyter 环境.实际上，经典的 Jupyter 和 Jupyter Hub 都提供了相当方便的开发环境，包括自动完成、代码高亮等功能.

要在本地启动 Jupyter，请进入课程目录，并执行：

```bash
jupyter notebook
```
或
```bash
jupyterhub
```
然后，您可以导航到任何 `.ipynb` 文件，打开它们并开始工作.

### 在容器中运行

Python 安装的另一种替代方案是将代码运行在容器中.由于我们的仓库包含一个特殊的 `.devcontainer` 文件夹，该文件夹指示如何为此仓库构建容器，VS Code 会建议您在容器中重新打开代码.这将需要安装 Docker，并且也会更加复杂，因此我们推荐给更有经验的用户.

## 在云端运行

如果您不想在本地安装 Python，并且有访问某些云资源的权限，一个不错的选择是在云端运行代码.您有几种方式可以做到这一点：

* 使用 **[GitHub Codespaces](https://github.com/features/codespaces)**，这是在 GitHub 上为您创建的虚拟环境，可以通过 VS Code 的浏览器界面访问.如果您有 Codespaces 的访问权限，只需点击仓库中的 **Code** 按钮，启动一个 codespace，即可立即开始.
* 使用 **[Binder](https://mybinder.org/v2/gh/microsoft/ai-for-beginners/HEAD)**.[Binder](https://mybinder.org) 是一个免费的云端计算资源，提供给像您这样的人在 GitHub 上测试一些代码使用.在前端页面有一个按钮可以在 Binder 中打开仓库 —— 这将迅速带您到 Binder 站点，它将构建底层容器并无缝启动 Jupyter 网页界面.

> **注意**: 为了防止滥用，Binder 会阻止访问某些网络资源.这可能会导致部分代码无法工作，例如从公共互联网获取模型和/或数据集.您可能需要寻找一些解决方法.此外，Binder 提供的计算资源相当基础，因此训练会很慢，尤其是在后期更复杂的课程中.

## 在带 GPU 的云端运行

本课程的一些后期课程将大大受益于 GPU 支持，否则训练将会异常缓慢.您可以选择以下几种选项，特别是如果您通过 [Azure for Students](https://azure.microsoft.com/free/students/?WT.mc_id=academic-77998-cacaste) 或您的机构访问云资源：

* 创建 [Data Science Virtual Machine](https://docs.microsoft.com/learn/modules/intro-to-azure-data-science-virtual-machine/?WT.mc_id=academic-77998-cacaste) 并通过 Jupyter 连接到它.然后，您可以将仓库克隆到机器上，开始学习.NC 系列虚拟机支持 GPU.

> **注意**: 某些订阅，包括 Azure for Students，默认不提供 GPU 支持.您可能需要通过技术支持请求额外的 GPU 核心.

* 创建 [Azure Machine Learning Workspace](https://azure.microsoft.com/services/machine-learning/?WT.mc_id=academic-77998-cacaste)，然后在那里使用 Notebook 功能.[这段视频](https://azure-for-academics.github.io/quickstart/azureml-papers/) 展示了如何将仓库克隆到 Azure ML 笔记本中并开始使用.

您还可以使用 Google Colab，它提供一些免费的 GPU 支持，并将 Jupyter 笔记本上传到那里逐个执行.