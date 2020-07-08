# 实验室 1B：使用 Azure 机器学习工具

在本实验室中，你将探索用于与 Azure 机器学习工作区结合使用的各种工具。

## 开始前

在开始本实验室之前，必须按照[上一个实验室](Lab01A.md)中的说明创建 Azure 机器学习工作区。

## 任务 1：在计算实例中使用 Azure ML SDK

可以在*工作室*界面中执行大多数资产管理任务以设置环境，但是能够编写配置任务的脚本以使其易于重复和自动执行也很重要。

1. 在 [Azure 机器学习工作室](https://ml.azure.com)中，在工作区的 **“计算”** 页上，查看 **“计算实例”** 选项卡，并根据需要定期单击 **“刷新”**，直到你在上一个实验中创建的计算实例启动为止。
2. 在浏览器中刷新 Azure 机器学习工作室网页，确保身份验证会话未过期。然后单击计算实例的 **Jupyter** 链接，以在新的标签页中打开 Jupyter Notebook。如果出现提示，请使用与你的 Azure 订阅相关联的 Microsoft 帐户登录。
3. 在笔记本环境中，创建一个新的 **“终端”**。 这将打开一个带有命令外壳的新选项卡。
4. Azure 机器学习 SDK 已安装在计算实例映像中，但是最好确保你具有最新版本，它包含本课程中需要的可选包；因此，请输入以下命令以更新 SDK 包：

    ```bash
    pip install --upgrade azureml-sdk[notebooks,automl,explain]
    ```

    安装软件包依赖项时，你可能会看到一些警告。你可以忽略这些消息。

    > **更多信息**： 有关安装 Azure ML SDK 机器可选组件的更多详细信息，请参阅 [Azure ML SDK 文档](https://docs.microsoft.com/python/api/overview/azure/ml/install?view=azure-ml-py)。

5. 接下来，运行以下命令，以将当前目录更改为 **“Users”** 目录，然后检索将在本课程的实验中使用的笔记本：

    ```bash
    cd Users
    git clone https://github.com/MicrosoftLearning/DP100
    ```

6. 该命令运行完毕后，关闭终端选项卡，然后在 Jupyter Notebook 文件浏览器中查看主页。然后打开 **“Users”** 文件夹 - 它应包含一个 **“DP100”** 文件夹，其中包含你在本实验其余部分将使用的文件。
7. 在 **“Users/DP100”** 文件夹中，打开 **“01B - Intro to the Azure ML SDK.ipynb”** 笔记本。然后阅读笔记本中的笔记，依次运行每个代码单元。
8. 笔记本中的代码运行完毕后，在 **“文件”** 菜单上单击 **“关闭并停止”** 以关闭它及其 Python 内核。然后关闭所有 Jupyter 浏览器选项卡。
9. 如果你当天完成了 Azure 机器学习的使用，请在 Azure 机器学习工作室的 **“计算”** 页面上，选择你的计算实例，然后单击 **“停止”** 以将其关闭。否则，让它继续运行以进行下一个实验室。

## 任务 2：设置 Visual Studio Codespace

Azure 机器学习中的计算实例提供易于管理的 Python 环境，让你无需管理自己的 Python 安装即可使用 Azure ML。但是，有时你可能想使用自己的图形化 Python 开发环境。在本课程中，我们将使用 Visual Studio Codespace 来简化安装，但是在任何 Python 环境中使用 Azure 机器学习 SDK 的原则都是相同的。

> **注意**： 撰写本文时，Visual Studio Codespace 处于*预览*阶段。你可能会遇到一些意外的错误消息。

1. 在新的浏览器选项卡中，导航到 [https://online.visualstudio.com](https://online.visualstudio.com)。如果系统提示，使用登录 Azure 时所用的 Microsoft 凭据登录 Visual Studio Codespace。
2. 使用以下设置创建一个代码空间（如果你还没有 Visual Studio Codespace 计划，请在出现提示时创建一个计划，该计划用于跟踪代码空间的资源利用率）：
    - **代码空间名称**： *你选择的唯一名称*
    - **Git 存储库**： MicrosoftLearning/DP100
    - **实例类型**： 标准 (Linux)
    - **挂起空闲代码空间之前的分钟数**： 60 分钟
3.  等待创建代码空间。这将打开基于浏览器的 Visual Studio Code 实例。
4. 等待一分钟左右，以便为你准备好环境。看起来好像什么都没发生，但是在后台，我们正在安装一些扩展，这些扩展将在实验室中使用。你会看到以下情况：
    - 准备好代码空间时，将打开一个脚本窗格以显示状态。
    - 将加载 Visual Studio Code 界面。
    - 此存储库中的文件将显示在左侧窗格中。
5. 成功完成安装后，你可以关闭 **“创建日志”** 窗格。

    Visual Studio Codespace 是 Visual Studio Code 的托管实例，可在 Web 浏览器中使用。Visual Studio Code 是一个通用代码编辑环境，可通过安装*扩展*来支持各种编程语言。要使用 Python，需要 Microsoft Python 扩展；从 **DP100** 存储库创建此环境时将为你安装此扩展及一些常用的 Python 包。

    该代码空间包括一个 Python 安装程序（版本 3.x），其中包括常见的软件包以及对 Visual Studio Code 界面内 Jupyter Notebooks 的支持。若要运行与 Azure 机器学习一起使用的代码，只需安装 Azure ML SDK。

6. 在 Visual Studio Codespace 的“应用程序”菜单 (**&#9776;**) 中，在 **“视图”** 菜单上，单击 **“命令面板”** （或按 CTRL+SHIFT+P）。然后在面板中输入命令 **Python:Create Terminal**。 这将在界面底部打开一个 Python 终端窗格。
7. 在终端窗格，使用此命令并输入以下命令来安装 Azure 机器学习 SDK（以及额外的可选 *“notebooks”* 软件包）：

    ```bash
    pip install azureml-sdk[notebooks]
    ```

8. 关闭“终端”窗格。

## 任务 3：在 Visual Studio Codespaces 中使用 Azure ML SDK

现在你已具有 Python 开发环境，可以在其中使用 Azure 机器学习 SDK。首先，需要获取连接到 Azure 机器学习工作区所需的配置信息。

1. 在新的浏览器选项卡中，打开 Azure 门户 ([https://portal.azure.com](https://portal.azure.com))，并根据需要登录。
2. 打开你在上一个实验中创建的 Azure 机器学习工作区资源，在其 **“概述”** 页上单击 **“下载 config.json”**，将该文件下载到本地计算机。
3. 在你的本地计算机上，将下载的 **config.json** 文件拖动到浏览器中的代码空间，然后将其放在笔记本文件中。这将上传配置文件，并在代码空间编辑器中将其打开。
4. 查看 config.json 文件的内容，然后将其关闭。
5. 在代码空间中，打开 **“01B - Intro to the Azure ML SDK.ipynb”** 笔记本 - 将在 Jupyter Notebook 界面中加载此笔记本。第一次使用 Jupyter Notebook 界面时，加载可能会花费一定时间，并且你可能会看到两个窗格 - 一个包含笔记本的 JSON 表示形式，另一个包含笔记本可视界面。
6. 当加载笔记本后，阅读其中的笔记，然后依次运行每个代码单元格，与在 Azure 机器学习 Notebook VM Jupyter 环境中的操作一样。

## 任务 4：使用 Visual Studio Code Azure 机器学习扩展

如果你计划在 Visual Studio Codespace（或 Visual Studio Code 的本地安装）中使用 Azure 机器学习，“Azure 机器学习”扩展可以帮助你更轻松地使用工作区中的资源，让你无需在代码开发环境和 Azure 机器学习工作室 Web 界面之间切换。

1. 在 Visual Studio Codespace 界面中，单击 **“扩展”** 选项卡 (&#8862;)，并搜索“Azure 机器学习”。然后从 Microsoft 安装 **“Azure 机器学习”** 扩展。安装扩展后，单击 **“需要重新加载”** 按钮，以使用该扩展重新加载环境。
2. 在 Visual Studio Codespace 界面中，单击 **“Azure”** 选项卡 (***&Delta;***)，在 **“Azure 机器学习”** 部分，展开订阅和 Azure 机器学习工作区。
3. 展开 **“计算群集”** 并验证是否列出了你在工作区中创建的 **“aml-cluster”** 计算资源以及 **“local”** 计算资源，在本例中，后者表示托管代码空间环境 - 你可以在本地计算机和在工作区中定义的计算资源上运行 Azure 机器学习代码试验。
4. 关闭“Visual Studio Codespace 浏览器”选项卡。
