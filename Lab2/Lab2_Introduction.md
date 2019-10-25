---
lab:
    title: '实验 2 - 注册和部署 ML 模型'
    module: '模块 2:使用 Azure 机器学习服务执行数据科学'
---

# 实验 2 - 注册和部署 ML 模型

## 实验 2.0：目标

在本实验中，你将：

- 使用 Azure 机器学习服务训练模型。
- 将创建的模型注册到工作区中的注册表
- 创建模型评分脚本
- 创建 YAML 文件，用于配置 Python 模块依赖项
- 创建容器映像
- 将模型部署为 Web 服务
- 使用已部署模型对新数据进行评分


## 简介

在本实验中，你将使用 Azure 机器学习服务及其 Python SDK 在 Azure 上训练上一个实验中开发的模型。完成训练后，将模型注册到注册表，并执行将模型部署到 Azure 机器学习服务所需的步骤，以便使用该模型。 

## 实验 2：资源

你将使用实验文件夹中的以下文件：

名称                            | 说明
----                            | -----------
Starter_Lab2_Notebook.ipynb     | 应使用的实验笔记本。  将笔记本导入 Notebook 项目并打开它。 


要获取有关创建 Azure Notebooks 项目和导入笔记本的帮助，请参阅 https://docs.microsoft.com/zh-cn/azure/notebooks/quickstart-migrate-local-jupyter-notebook

要获取有关将数据上传到 Azure Notebooks 的帮助，请参阅 https://docs.microsoft.com/zh-cn/azure/notebooks/work-with-project-data-files



## 前提条件

需要满足以下前提条件，才能进行本实验：
- 注册免费的 Azure Notebooks 服务。  
- 拥有可以预配 Azure 机器学习服务工作区的 Azure 订阅。
