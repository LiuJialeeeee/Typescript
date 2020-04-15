# Typescript 官方文档学习笔记

## 1. 目标

作为一个计算机小白,我现在仅是刚接触了前端开发,前置知识也仅是一些c++的简单应用.在前不久也仅是囫囵吞枣的学了一遍javascript.甚至连API的调用都不是很熟悉.鉴于此,我想要重新梳理一下js知识且通过TypeScript来和之前学习的c++产生一个联系,并由此**巩固js基础**.

## 2. 流程简介

我的学习流程将会**顺着官方文档逐一推进**,中间可能会**参考*javascript高级程序设计***.

主要**目标**还是学习 Typescript 的特性,所以我会先沿着官方手册的顺序记录笔记,再通过 *javascript高级程序设计*补充内容.个人思考估计会很少.

## 3. 安装流程

1. node官网安装node.js环境

   ​	打开命令行	//win + r 跳出的窗口中输入 powershell 即可

   ​	之后分别输入

   ​	node -v

    	npm -v 

   ​	如果出现版本号

   ​	即说明安装成功

2. 安装Typescript 包

   ​	在命令行输入

```命令行
npm install typescript -g
tsc --version
```

3. 安装VScode

   ​	百度搜索vscode

   ​	找到官网就随便下

## 4. vscode中的使用流程

1. 打开vscode

2. 新建文件后缀是 .ts的文件

3. 输入代码

   ```Typescript
   let a: string = 'hello';
   console.log(a);
   ```

4. 在 vscode 的左边资源管理器下的打开的编辑器中右击新建ts文件,选择在终端中打开

5. 在代码一栏的下面出现终端,输入: tsc 文件名 进行编译

6.  编译成功后在本文件夹下自动编译好一个js文件,通过刚打开的终端输入代码

   ```typescript
   node 新js文件名
   ```

7. 在命令行中出现我和你打招呼

日期:2020/04/11