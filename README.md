---
title: Claude+Cloud Studio念咒编程搭建Excel工资核算
subTitle: 用claude与cloud studio搭建excel核算表
date: '2023-7-23'
tags: ['用户体验']
summary: 本文我将使用Claude+Cloud Studio念咒编程搭建Excel工资核算。并且会将该项目作为模版，供大家使用。
isRecommend: true
description: 在 Serverless 技术背景下，应用的开发到部署这个过程，存在很大的优化空间。腾讯云DeployKit 帮忙开发者将自己的应用一键部署到 Serverless 平台。部署过程简单且快速，以满足应用高频部署的需求。
keywords: Cloud Studio,在线编程,WebIDE,CloudIDE,云端IDE,在线IDE,云端开发工具,在线集成开发环境,开发环境分享,代码托管,在线开发,在线调试,软件团队协作
---

**目录**

前言

一.实验准备

1.1 Cloud Studio介绍

1.2 GPT工具 Claude 介绍

1、背景介绍

2、接入方式

三、工资核算的实验案例介绍

规则如下

1、迟到次数核算方法：

2、个税扣除核算方法：

3、将算出的结果填充到salary.xlsx表中

4、新建一个文件将表格中的数据在Cloud Studio终端中输出

二.应用场景

2.1快速启动项目

三.登录注册

四.工作空间的创建与使用

4.1创建工作空间

4.1.1填写工作空间信息

4.2工作空间的使用

4.2.1工作空间界面简介

4.2.2管理工作空间

运行

停止

删除

恢复

*前言*


 *本文我将使用Claude+Cloud Studio念咒编程搭建Excel工资核算。并且会将该项目作为模版，供大家使用。*

先来看一下效果


![](https://help-assets-1257242599.cos.ap-shanghai.myqcloud.com/enterprise/2023/2/2-2.png)

![](https://help-assets-1257242599.cos.ap-shanghai.myqcloud.com/enterprise/2023/2/2-3.png)

# 一.实验准备

**1.1 Cloud Studio介绍**


Cloud Studio 是基于浏览器的集成式开发环境(IDE)，为开发者提供了一个永不间断的云端工作站。用户在使用CloudStudio 时无需安 装，随时随地打开浏览器就能在线编程。


![](https://help-assets-1257242599.cos.ap-shanghai.myqcloud.com/enterprise/2023/2/2-5.png)


​编辑大家也看到了，很多模版以及环境都有提供，今天给大家演示编程搭建Excel工资核算，选用python模板，刚上手可能确实不太会，但熟悉了一会，就发现他的好处了。

Cloud Studio 作为在线IDE，包含代码高亮、自动补全、Git集成、终端等IDE的基础功能，同时支持实时调试、插件扩展等，可以帮助开发者快速完成各种应用的开发、编译与部署工作。我将这次的这个博客网站使用Cloud Studio推送到了Gitee，[大家可以访问](https://gitee.com/li-jian0531/cloud-studio)


![](https://help-assets-1257242599.cos.ap-shanghai.myqcloud.com/enterprise/2023/2/2-6.png)


**1.2 GPT工具 Claude 介绍**

*1、背景介绍*

是由Anthropic创建的（Anthropic是一家由对公司不满意的前 OpenAI 工程师创立的初创公司），它的功能尚未像 **GPT** 那样全面，但无需搜索网络即可响应。它的优势包括消化、总结财务文件和研究论文。Claude 得到了 Google、Zoom 和 Slack 的支持。
 **Claude** 是Anthropic的人工智能助手，可通过聊天界面或 API 访问。它能够进行对话和文本处理。用例包括摘要、搜索、创意和协作写作、制定问答和一些基本编码。由前 **OpenAI** 员工开发，它的研究起点也是**GPT-3**，相同的团队背景、技术线路和应用方向。现在用户可以通过Quora的Poe应用程序以及其他两个聊天机器人访问 **Claude**。
 它可以快速响应客户服务请求，并可以在需要时将任务交给人工。**Claude**特别擅长编辑、重写、总结、分类和提取结构化数据。它还可以遵循基本指令和逻辑场景，根据年度报告分析战略风险和机遇，评估立法的利弊并识别法律文件中的风险。

 *2、接入方式*

 [claude](https://www.anthropic.com/)的官网在国内虽然不太好访问，但是这个并不影响我们使用它，相信在网上有很多如何接入 Claude 的方法，这里我也介绍一下，前面背景介绍里说过了，Slack 也在支持 Claude，我们只需要在 Slack 插件中加入它即可。关于 Slack 如何去创建一个组织大家可以自行搜索查询，这里我们为了各位实验的便利性，创建了一个临时的 Slack 组织，在手册中点击[邀请链接](https://app.slack.com/client/T053LBM9STT)即可加入我们临时的 **Slack** 组织


 ![](https://help-assets-1257242599.cos.ap-shanghai.myqcloud.com/enterprise/2023/2/2-7.png)

 这里使用企业微信和个人微信都可以。

加入组织后，你们可以看到 **Slack** 的面板，**Claude** 应用我们已经添加到组织中了，大家可以随时启用

# 三、工资核算的实验案例介绍


 ![](https://help-assets-1257242599.cos.ap-shanghai.myqcloud.com/enterprise/2023/2/2-8.png)

 由于实验关系，我们来一个比较简单的工资核算的例子（不去测算五险一金）
 请运用财务部门提供的数据（salary.xlsx)，根据表格中的数据核算出最终每个人的实发工资。

**规则如下**

-当前表格中，**考勤扣除金额**、**个税扣除**、**实发工资**目前是空缺的，最终生成的数据需要将上述三列的数据分别根据以下规则填充。

**1、迟到次数核算方法:**


-3次以内不扣除


-3次以上每多1次扣除100（也就是第4次开始）


**2、个税扣除核算方法：**


**个税扣除 = 基础工资 - 五险一金扣除 - 考勤扣除金额**，然后进行以下方式核算：


-不考虑个税起征点。


-收入中不超过3000元的按3%税率缴纳个税。


-3000元-12000元的按10%税率缴纳个税。


-超过12000元不高于25000元的按税率20%计算。


-25000元-35000元的按税率25%计算。


-35000元-55000元的按税率30%计算。


-55000元-80000元的按税率35%计算。


**3、将算出的结果填充到salary.xlsx表中**


-考前扣除金额填充至原文件中。


-个税扣除填充至原文件中。


-实发工资填充至原文件中。


**4、新建一个文件将表格中的数据在Cloud Studio终端中输出**



# 二.应用场景

Cloud Studio 在线编程工具适用于以下几个场景：

**2.1快速启动项目**


使用 Cloud Studio 的预置环境，您可以直接创建对应类型的工作空间，快速启动项目进入开发状态，无需进行繁琐的环境配置。

下面就是我的工作空间，大家可以下次使用的时候，进入对应的工作空间，就可以继续编写代码，很是方便。


# 三.登录注册


Cloud Studio 在线编程平台支持使用[CODING (opens new window)](https://coding.net/?from_column=20420&from=20420)账号和 GitHub 账号，以及微信登录，可以在[登录 (opens new window)](https://cloudstudio.net/auth/realms/cloudstudio/protocol/openid-connect/auth?client_id=cloudstudio-apiserver&response_type=code&redirect_uri=https%3A%2F%2Foauth.cloudstudio.net%2Fapi%2Fpublic%2Foauth%2Fcallback%3Fsrc%3D%252F&team=&kc_idp_hint=)
界面输入相应的账号登录前往 Web IDE，这里我用的是微信登录。



# 四.工作空间的创建与使用

一个工作空间是一个虚拟计算单元，它包含独立的存储、计算资源以及开发环境。Cloud Studio 是以工作空间来组织的，本文为您介绍如何创建工作空间。

**4.1创建工作空间**

进入 Cloud Studio 云端 IDE，可以通过两种方式创建工作空间，**第一种方式**：点击模板直接创建工作空间，**第二种方式**：单击【新建工作空间】，进入工作空间创建页面

*4.1.1填写工作空间信息*

第一种方式点击模板创建工作空间，可自动生成工作空间名称，并运行模板的预置环境及样本代码。这里我用的是Flutter。


第二种方式，选择创建工作空间，然后选择预置环境，填写工作空间名、描述，并选择运行环境和代码来源。



-**工作空间名**：您的工作空间的唯一标识，只能由字母、数字、下划线（_）、中划线（-）、点（.）组成，不能包含空格或其它字符。


-**描述**：对该工作空间作用的描述。


-**运行环境**：工作空间内代码运行的环境，您可以选择预置环境，包含 Ubuntu、Python、Java 和 Node.js 四种；也可以选择将其连接到自己的云服务器上。


-**代码来源**：工作空间内的代码来源，此处我们选择“空”，即不添加任何代码。

单击【创建】按钮，即可完成工作空间的创建。您还可以创建代码来自于 Git 仓库的工作空间，代码会被自动克隆到工作空间


**4.2工作空间的使用**


您可以在 Cloud Studio 云端 IDE 的工作空间内存放自己的项目代码，安装所需要的软件环境，运行或编译项目，本文为您介绍如何使用工作空间。

注意：

-**数量限制**：目前每个用户最多可以创建 10 个工作空间，并且只能同时运行一个工作空间，如果您需要打开另一个工作空间需要先关闭当前运行中的工作空间。


-**时间限制**：每个用户每月可以免费使用工作空间共 1000 分钟，超出时间将产生扣费（连接云主机的工作空间无此限制）。


*4.2.1工作空间界面简介*

工作空间是我们主要的工作区域，主要由顶部菜单栏、左侧操作面板、右侧代码编辑区和底部状态栏组成。

您可以根据自己的习惯设置界面外观、偏好，安装自己需要的插件。

需要注意的是，您的**偏好设置和插件在每个工作空间中是互相隔离**的，也就是说您可以给不同的工作空间设置不同的偏好，安装不同的插件。这里面大部分和你在本地使用vscode是一样的。


我们可以通过终端来进行这些操作，点击菜单栏--终端--新终端，会在底部打开一个面板，点击【终端】切换到终端。


*4.2.2管理工作空间*


在 Cloud Studio 云端 IDE 的工作空间列表页面，您可以运行、停止、删除和恢复工作空间。


**运行**


单击对应的工作空间卡片，就会在新的页面打开并运行该空间，此时该工作空间卡片上会显示“运行中”状态。

![](https://help-assets-1257242599.cos.ap-shanghai.myqcloud.com/enterprise/2023/2/2-9.png)



**停止**


对于处在“运行中”状态的工作空间，单击卡片右边的【停止】，就可以停止运行该工作空间。


![](https://help-assets-1257242599.cos.ap-shanghai.myqcloud.com/enterprise/2023/2/2-10.png)



**删除**


您可以删除未运行的工作空间，单击工作空间卡片右下角的【删除】即可删除。


![](https://help-assets-1257242599.cos.ap-shanghai.myqcloud.com/enterprise/2023/2/2-11.png)


**恢复**


为了防止误删除，已删除的工作空间会展示在下方“已删除的工作空间”列表中，保留24小时。在此之前您可以随时单击【恢复】，还原您的工作空间，超过 24 小时未恢复的工作空间将被永远销毁。


![](https://help-assets-1257242599.cos.ap-shanghai.myqcloud.com/enterprise/2023/2/2-12.png)


# 五.代码展示与运行


```shell
import pandas as pd

# 读取excel文件
df = pd.read_excel('salary.xlsx',sheet_name='Sheet1')

# 计算考勤扣除金额
late_counts = df['迟到次数']

df['考勤扣除金额'] =  late_counts.apply(lambda x: max((x-3)*100 ,0))

#计算个税扣除
taxable_income = df['工资基数'] - df['五险一金扣除'] - df['考勤扣除金额']
df['个税扣除']= taxable_income.apply(lambda x:
min(x*0.03,90) if x <=3000 else
min(x*0.1,210) if 3000<x<=12000 else
min(x*0.2,1410) if 12000<x<=25000 else
min(x*0.25,2660) if 25000<x<=35000 else
min(x*0.3,4410) if 35000<X<=55000 else
min(x*0.35,7160) if 55000<x<-80000 else
X *0.45)
#计算实发工资
df['实发工资']= df['工资基数'] - df['五险一金扣除'] - df['考勤扣除金额'] - df['个税扣除']


# 打印整体数据
print(df)

# 将数据写回到excel文件

writer = pd.ExcelWriter('salary_output.xlsx')
df.to_excel(writer, 'Sheet1', index=False) 
writer.close()

print('结果已写入Excel!')
```

![](https://help-assets-1257242599.cos.ap-shanghai.myqcloud.com/enterprise/2023/2/2-13.png)







