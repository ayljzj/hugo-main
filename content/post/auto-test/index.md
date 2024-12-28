---
layout: post
title: 自动推理（实验相关内容）
subtitle: ' "实验"'
date: 2024-12-26
author: AYLj
catalog: true
categories:
  - 自动推理
---

> “Work. ”

## 前言

无<br>
## 1、相关代码修改（基础项）
### 基础代码修改项

| **必改项**           |                                                   |                                                   |
| :---------------- | :------------------------------------------------ | :------------------------------------------------ |
| 2217              | Resolution.cpp                                    | for(int i=0;i<cla->uLitNum;++1i){删除1              |
|                   | 使用776行的main函数                                     | 替换原始800行的main函数                                   |
|                   |                                                   |                                                   |
| 验证检查              | 原始代码                                              | 修改后，会生成run文件                                      |
| Prover.cpp<br>319 | if(1){<br>        FileOp::delRunFiles();<br>    } | if(0){<br>        FileOp::delRunFiles();<br>    } |
|                   |                                                   |                                                   |
| **选改项**           |                                                   |                                                   |
| main.cpp          | debug                                             | 编译release                                         |
| 216               | \#define newTriDebug                              | //#define newTriDebug                             |
| 755               | //child = fork();<br>    if (0 == 0)              | child = fork();<br>if (child == 0) {              |
|                   |                                                   | 生成文件                                              |


文字变元输出<br>
```
cout<< QLit->subTerm->ToString()<<endl;//debug输出当前文字项
cout<<QLit->subTerm->ToStringBind()<<endl;//debug输出当前文字项和变元元替换项
```


### 命令行版本测试命令
测试CSE和Eprover融合系统命令：<br>
```
java -jar mcs_epr.jar CSE_E problems 0 1 4 1 300 0 1 10
```


测试CSE和Vampire融合系统命令：
```
java -jar mcs_vampire.jar CSE_V problems 0 1 2 1 260 30 1 10
```


单独测试CSE系统命令：
```
java -jar mcs_scs.jar CSE problems 0 1 0 1 1 150
```
其中260 20 为时间参数
如果那两个数值变为300 0，意味着是原始测出来的数据，
前一个数值代表eprover测的时间，后一个数值代表CSE测的时间，
300秒减去前两个数值所剩下的时间也是eprover参与的
