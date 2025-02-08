---
title: JavaScript
date: 2024-09-06 06:21:31
tags:
---

JavaScript 学习笔记


<!-- more -->

前端技术组成：HTML、CSS、JavaScript

什么是 HTML ？

HTML (HyperText Markup Language) 超文本标记语言

决定网页的结构和内容，相当于人的身体

什么是 CSS ？

CSS (Cascading Style Sheets) 串联样式表

决定网页呈现给用户的模样，相当于人的衣服、妆容

什么是 JavaScript ？

JavaScript是Web开发领域中的一种功能强大的编程语言，主要用于开发交互式的网页。我们在计算机、手机等设备上浏览的网页，其多数交互逻辑都可以通过JavaScript实现。


实现业务逻辑和页面控制，相当于人的各种动作

常见的 JavaScript 交互效果

[https://www.vmall.com/index.html](https://www.vmall.com/index.html)
[https://map.baidu.com/](https://map.baidu.com/)

- 轮播图
- 商品分类（隐藏的二级分类）
- 选项卡
- 表单验证
- 等等


1995年 网景通信公司（Netscape Communications Corporation，简称网景公司）为网景导航者（Netscape Navigator）浏览器开发了JavaScript语言。

1996年 网景公司在网景导航者2.0浏览器中正式内置了JavaScript语言。后来，网景公司将JavaScript语言提交ECMA国际（前身为欧洲计算机制造商协会），希望JavaScript能够成为国际标准。


ECMAScript 1.0（1997年6月）：这是ECMAScript的第一个版本，标志着JavaScript开始走向标准化

ECMAScript 2.0（1998年6月）： 相对于1.0版本，ECMAScript 2.0进行了小幅度的改动，进一步完善了语言规范。

ECMAScript 3.0（1999年12月）：ECMAScript 3.0成为了JavaScript的通行标准，得到了广泛支持。

ECMAScript 4.0（未正式发布）：2007年10月，ECMAScript 4.0的草案发布，对3.0版本进行了大幅升级。然而，由于目标过于激进，各方对于是否通过该标准产生了严重分歧。最终，ECMA决定中止ECMAScript 4.0的开发。

ECMAScript 5（原名ECMAScript 3.1，2009年12月）：由于ECMAScript 4.0的开发被中止，ECMA将其中涉及现有功能改善的一小部分发布为ECMAScript 3.1，后改名为ECMAScript 5。ECMAScript 5引入了严格模式、JSON支持等新特性，进一步提升了JavaScript的健壮性和可用性

ECMAScript 5.1（2011年6月）：ECMAScript 5.1是ECMAScript 5的小幅修改版本，于2011年6月发布，并成为ISO国际标准（ISO/IEC 16262:2011）。

ECMAScript 6（ES2015，2015年6月）：ECMAScript 6（简称ES6或ES2015）是JavaScript的下一个重大更新版本，于2015年6月正式发布。它引入了class、箭头函数、模块、Promise等新特性，极大地丰富了JavaScript的语法和功能。


自ECMAScript 6之后，ECMA每年都会发布一个新版本的ECMAScript标准。例如，ECMAScript 2016（ES7）、ECMAScript 2017（ES8）等。这些新版本在保持与旧版本兼容性的同时，不断引入新的特性和改进，以推动JavaScript语言的持续发展和进步。


https://262.ecma-international.org/


JavaScript和Java的关系

没关系

JavaScript和Java只是名字相似，本质上是完全不同的两种语言。


ECMA国际是一个国际性会员制的信息和电信标准组织，该组织发布了ECMA-262标准文件，规定了浏览器脚本语言的标准，并将这种语言称为ECMAScript。JavaScript可以理解为ECMAScript的实现和扩展。


JavaScript是由ECMAScript、DOM、BOM这3部分组成的。

ECMAScript：规定了JavaScript的编程语法和基础核心内容，是所有浏览器厂商共同遵守的一套JavaScript语法工业标准。

DOM：文档对象模型，是W3C组织制定的用于处理HTML文档和XML文档的编程接口，它提供了对文档的结构化表述，并定义了一种方式使程序可以对该结构进行访问，从而改变文档的结构、样式和内容。

BOM：浏览器对象模型，是一套编程接口，用于对浏览器进行操作，如刷新页面、弹出警告框、控制页面跳转等。


JavaScript的特点

简单易用

JavaScript是一门脚本语言（Script Language），语法规则比较松散，使开发人员能够快速完成程序的编写工作

可以跨平台

JavaScript语言不依赖操作系统，仅需要浏览器的支持

支持面向对象

面向对象是软件开发中的一种重要的编程思想，JavaScript能够通过面向对象思想进行编程。

开发工具

浏览器：用于执行、调试JavaScript代码。

代码编辑器：用于编写代码
