---
lab:
    title: '实验 3 - 使用 AutoML 和 HyperDrive'
    module: '模块 3:使用 Azure 机器学习服务实现机器学习自动化'
---

# 实验 3 - 使用 AutoML 和 HyperDrive

## 实验 3.0：目标

在本实验中，你将：

- 了解机器学习管道
- 了解 Azure 机器学习服务 AutoML 和 Hyperdrive
- 创建一个 Python 脚本，这个脚本使用 Azure 机器学习服务的 AutoML 来推荐模型
- 测试 Python 脚本推荐的模型



## 简介

在本实验中，你想了解是否有比之前手动创建的模型性能更优越的模型。你决定使用 Azure 机器学习服务的 AutoML 和 HyperDrive 同时执行多个不同类型的分类模型，比较它们的结果，并推荐性能最佳的模型。这将为你节省大量选择最佳模型的时间，以便你可以更快交付解决方案。 

## 实验 3：资源

你将使用实验文件夹中的以下文件：

名称                            | 说明
----                            | -----------
Starter_Lab3_Notebook.ipynb     | 应使用的实验笔记本。  将笔记本导入 Notebook 项目并打开它。 


要获取有关创建 Azure Notebooks 项目和导入笔记本的帮助，请参阅 https://docs.microsoft.com/zh-cn/azure/notebooks/quickstart-migrate-local-jupyter-notebook

要获取有关将数据上传到 Azure Notebooks 的帮助，请参阅 https://docs.microsoft.com/zh-cn/azure/notebooks/work-with-project-data-files



## 前提条件

需要满足以下前提条件，才能进行本实验：
- 注册免费的 Azure Notebooks 服务。  
- 拥有可以预配 Azure 机器学习服务工作区的 Azure 订阅。
