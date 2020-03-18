# 实验 1B：使用 Azure 机器学习工具

在本实验中，你将探索用于与 Azure 机器学习工作区结合使用的各种工具。

## 开始前

在开始本实验之前，必须按照[上一个实验](Lab01A.md)中的说明创建 Azure 机器学习工作区。

## 任务 1：在计算实例中使用 Azure ML SDK

可以在工*作室*界面中执行大多数资产管理任务以设置环境，但是能够编写配置任务的脚本以使其易于重复和自动执行也很重要。

1. 在 [Azure 机器学习工作室](https://ml.azure.com)中，在工作区的 **“计算”** 页上，查看 **“计算实例”** 选项卡，并根据需要定期单击 **“刷新”**，直到你在上一个实验中创建的计算实例启动为止。
2. 在浏览器中刷新 Azure 机器学习工作室网页，确保身份验证会话未过期。然后单击计算实例的 **Jupyter** 链接，以在新的标签页中打开 Jupyter Notebook。如果出现提示，请使用与你的 Azure 订阅相关联的 Microsoft 帐户登录。
3. 在笔记本环境中，创建一个新的 **“终端”**。这将打开一个带有命令外壳的新选项卡。
4. Azure 机器学习 SDK 已安装在计算实例映像中，但是最好确保你具有最新版本，它包含本课程中需要的可选包；因此，请输入以下命令以更新 SDK 包：

    ```bash
    pip install --upgrade azureml-sdk[notebooks,automl,explain]
    ```

    > **更多信息**：有关安装 Azure ML SDK 机器可选组件的更多详细信息，请参阅 [Azure ML SDK 文档](https://docs.microsoft.com/python/api/overview/azure/ml/install?view=azure-ml-py)。

5. 接下来，运行以下命令，以将当前目录更改为 **“Users”** 目录，然后检索将在本课程的实验中使用的笔记本：

    ```bash
    cd Users
    git clone https://github.com/MicrosoftLearning/DP100
    ```

6. 该命令运行完毕后，关闭终端选项卡，然后在 Jupyter Notebook 文件浏览器中查看主页。然后打开 **“Users”** 文件夹 - 它应包含一个 **“DP100”** 文件夹，其中包含你在本实验其余部分将使用的文件。
7. 在 **“Users/DP100”** 文件夹中，打开 **“01B - Intro to the Azure ML SDK.ipynb”** 笔记本。然后阅读笔记本中的笔记，依次运行每个代码单元。
8. 笔记本中的代码运行完毕后，在 **“文件”** 菜单上单击 **“关闭并停止”** 以关闭它及其 Python 内核。然后关闭所有 Jupyter 浏览器选项卡。
9. 在 Azure 机器学习工作室中的 **“计算”** 页面上，选择计算实例，然后单击 **“停止”** 以将其关闭。

## 任务 2：设置 Visual Studio Online 环境

Azure 机器学习中的计算实例提供易于管理的 Python 环境，让你无需管理自己的 Python 安装即可使用 Azure ML。但是，有时你可能想使用自己的图形化 Python 开发环境。在本课程中，我们将使用 Visual Studio Online 来简化安装，但是在任何 Python 环境中使用 Azure 机器学习 SDK 的原则都是相同的。

> **注意**：撰写本文时，Visual Studio Online 处于 *预览* 阶段。你可能会遇到一些意外的错误消息。

1. 在新的浏览器选项卡中，导航到 [https://online.visualstudio.com](https://online.visualstudio.com)，并单击 **“开始”**。
2. 使用登录 Azure 时所用的 Microsoft 凭据登录 Visual Studio Online。
3. 使用以下设置 创建一个新环境，如果系统提示你在 Azure 订阅中创建计费计划，请先创建它：
    - **环境名称**：*你选择的唯一名称*
    - **Git 存储库**： MicrosoftLearning/DP100
    - **实例类型**：标准 (Linux)
    - **挂起空闲环境之前的分钟数**：30 分钟
4. 等待创建环境，然后单击其名称以进行连接。

    Visual Studio Online 是 Visual Studio Code 的托管实例，可在 Web 浏览器中使用。Visual Studio Code 是一个通用代码编辑环境，可通过安装*扩展*来支持各种编程语言。要使用 Python，需要 Microsoft Python 扩展；从 **DP100** 存储库创建此环境时将为你安装此扩展及一些常用的 Python 包。

    托管的 Visual Studio Code 环境包括三个 Python 安装（版本 2.7.13、3.5.3 和 3.8.0）。你将使用 Python **3.5.3** 虚拟环境。自行安装时，需要安装 Python、创建虚拟环境并安装所需的包。在本实验中，已为你安装大多数通用 Python 配置，但是你需要安装 Azure 机器学习 SDK。

5. 在 Visual Studio Online 环境中，等待加载 DP100 存储库的内容，然后在应用程序菜单 (**&#9776;**) 中的 **“视图”** 菜单上，单击 **“命令面板”** （或按 Ctrl+Shift+P）。然后在面板中输入命令 **Python: Create Terminal**。这将在 Visual Studio Online 界面底部打开一个 Python 终端窗格。

    > **提示**：如果未列出 *Python: Create Terminal* 命令，请刷新浏览器以重新加载环境并重试。

6. 在终端窗格中，输入以下命令以更改为在其中定义了 Python 3.5.3 虚拟环境的目录：

    ````bash
    cd /usr/bin
    ````

7. 现在使用此命令安装 Azure 机器学习 SDK（以及额外的可选 *“notebooks”* 包）：

    ```bash
    sudo pip install azureml-sdk[notebooks]
    ```

8. 关闭“终端”窗格。

## 任务 3：在 Visual Studio Online 中使用 Azure ML SDK

现在你已具有 Python 开发环境，可以在其中使用 Azure 机器学习 SDK。首先，需要获取连接到 Azure 机器学习工作区所需的配置信息。

1. 在新的浏览器选项卡中，打开 Azure 门户 ([https://portal.azure.com](https://portal.azure.com))，并根据需要登录。
2. 打开你在上一个实验中创建的 Azure 机器学习工作区资源，在其 **“概述”** 页上单击 **“下载 config.json”**，将该文件下载到本地计算机。
3. 在文本编辑器中打开下载的 **config.json** 文件，并将其内容复制到剪贴板。此文件包含连接到工作区所需的配置信息。
4. 在 Visual Studio Online 中，在 VS Online 工作区的根文件夹中创建一个名为 **config.json** 的新文件。
5. 在 Visual Studio Online 工作区中将复制的配置信息粘贴到新的 config.json 文件，然后保存它。
6. 在 Visual Studio Online 中，打开 **“01B - Intro to the Azure ML SDK.ipynb”** 笔记本 - 将在 Visual Studio Online 中的 Jupyter Notebook 界面中加载此笔记本。第一次使用 Jupyter Notebook 界面时，加载可能会花费一定时间，并且你可能会看到两个窗格 - 一个包含笔记本的 JSON 表示形式，另一个包含笔记本可视界面。
7. 笔记本加载完毕后，在 Visual Studio Online 界面的左下方，单击当前的 Python 虚拟环境。根据存储库中的配置设置，此环境应已更改为 **Python 3.5.3**，但仍请再次选择该虚拟环境（笔记本是使用其他版本编写的，其元数据中说明了这一点）。
8. 阅读笔记本中的笔记，依次运行每个代码单元，与在 Azure 机器学习 Notebook VM Jupyter 环境中的操作一样。

## 任务 4：使用 Visual Studio Code Azure 机器学习扩展

如果你计划在 Visual Studio Online（或 Visual Studio Code 的本地安装）中使用 Azure 机器学习，“Azure 机器学习”扩展可以帮助你更轻松地使用工作区中的资源，让你无需在代码开发环境和 Azure 机器学习工作室 Web 界面之间切换。

1. 在 Visual Studio Online 中，单击 **“扩展”** 选项卡 (&#8862;)，并搜索“Azure 机器学习”。然后从 Microsoft 安装 **“Azure 机器学习”** 扩展。安装扩展后，单击 **“需要重新加载”** 按钮，以使用该扩展重新加载环境。
2. 在 Visual Studio Online 中，单击 **“Azure”** 选项卡 (***&Delta;***)，在 **“Azure 机器学习”** 部分，展开订阅和 Azure 机器学习工作区。
3. 展开 **“计算”** 并验证是否列出了你在工作区中创建的 **“aml-cluster”** 计算资源以及 **“local”** 计算资源，在本例中，后者表示 Visual Studio Online 托管环境 - 你可以在本地计算机和在工作区中定义的计算资源上运行 Azure 机器学习代码试验。
4. 关闭“Visual Studio Online 浏览器”选项卡。
