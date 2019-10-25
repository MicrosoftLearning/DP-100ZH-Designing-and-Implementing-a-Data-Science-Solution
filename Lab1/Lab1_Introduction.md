---
lab:
    title: '实验 1 - 在 Azure Notebooks 中训练模型'
    module: '模块 1:在 Azure 上执行数据科学'
---

# 实验 1 - 在 Azure Notebooks 中训练模型

## 实验 1.0：目标

在本实验中，你将：

- 通过 Python 使用 Azure Notebooks（一项基于云的 Jupyter Notebook 服务）。
- 执行探索性数据分析
- 创建机器学习模型功能
- 训练基于开放源代码的分类预测性模型。

本实验的主要目标是让学生尽快熟练使用 Azure Notebooks 并开始处理 Adventure Works 用例。

## 简介

你将使用 Python 和开放源代码包 scikit-learn 在 Azure Notebooks 中训练分类模型。在此过程中，需要执行一些基本的探索性数据分析来理解数据。  然后，需要创建要在模型训练中使用的功能。最后，你将训练和评估模型。注意：  目前不会使用 Azure 服务。 

团队的数据工程师为你提供了 CSV 格式的数据提取文件，其中包含你需要的所有数据。  入门实验笔记本将指导你完成本实验所需执行的所有任务。 



## 实验 1：资源

你将使用实验文件夹中的以下文件：

名称                            | 说明
----                            | -----------
Starter_Lab1_Notebook.ipynb     | 应使用的实验笔记本。  将笔记本导入 Notebook 项目并打开它。 
AWData.csv                      | Adventure Works 数据提取文件。将此文件上传到 Azure Notebooks 项目。 

要获取有关创建 Azure Notebooks 项目和导入笔记本的帮助，请参阅 https://docs.microsoft.com/zh-cn/azure/notebooks/quickstart-migrate-local-jupyter-notebook

要获取有关将数据上传到 Azure Notebooks 的帮助，请参阅 https://docs.microsoft.com/zh-cn/azure/notebooks/work-with-project-data-files



## 前提条件

需要满足以下前提条件，才能进行本实验：
- 注册免费的 Azure Notebooks 服务。  
