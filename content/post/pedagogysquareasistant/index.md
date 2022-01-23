---
title: 教学立方辅助插件（更新至v2.1.1）
date: 2020-04-02
image: images/pedagogysquareasistant.png
author: LadderOperator
tags:
  - 技术向
---
# 教学立方辅助插件



> 由于官方已经注意到了本插件，本插件下载课件的核心原理已经被教学立方修复了，现在课件的链接是需要有权限验证的（即，每个账户对应有一个身份验证的串，如果后台不给你下载权限，你的验证串发送获取课件链接的请求会被阻止；如果你恰好有下载权限，才会给你合法的下载链接）。如果本身你无法下载的课件，那么本插件**现在无法**为你突破这一限制，但是可以帮你复制这一页上不在文件夹里的所有可下载文件链接；因此如果是为了突破下载，那么你可以卸载此插件了。

>

> 本插件主要目的是为了后台批改作业图片方便，且我尊重平台保护教师知识产权的这一决定，因此不会进一步去跟进此问题。



项目地址：[LadderOperator/PedagogySquareAsistant](https://github.com/LadderOperator/PedagogySquareAsistant)



【👍推荐】[新版Edge](https://www.microsoft.com/zh-cn/edge)商店下载地址：[教学立方辅助工具](https://microsoftedge.microsoft.com/addons/detail/%E6%95%99%E5%AD%A6%E7%AB%8B%E6%96%B9%E8%BE%85%E5%8A%A9%E5%B7%A5%E5%85%B7/dofkbbkfgccgjaieblngngfcbddibnkh)



谷歌商店下载地址：[教学立方辅助工具](https://chrome.google.com/webstore/detail/%E6%95%99%E5%AD%A6%E7%AB%8B%E6%96%B9%E8%BE%85%E5%8A%A9%E5%B7%A5%E5%85%B7/dpcoadobjphddblobamffijbelbkidga)



视频演示地址：[点击观看](http://mpvideo.qpic.cn/0bf2h4aagaaahuamkugeavpfap6dam7qaaya.f10002.mp4?dis_k=cff7834ed893cd138c5d291399d41f9b&dis_t=1592459265)



一键预览助教批改作业页面上传的图片等实用功能，同时可以把课件下载链接替换为真实链接以供全页下载。



> 所有课件均为任课老师的辛苦劳动付出，本插件使用者**仅可为了教学工作、课程学习方便之用，不得未经允许将课件在网络随意传播**！请珍惜老师的劳动成果和心血！（如果我发现任何一个人违反了这条，我会删去此功能）

>

> 此外需要说明的是，尽管这个插件没啥工作量，也必然会遇到版权之类的质疑，我仍然认为公开是合适的。校内网站的bug很多（包括曾经的教务网），以往是一上报就较快能修复或者注意，工作态度还挺认真的。但是教学立方这个产品已经实行有段日子了，周围学生和老师反馈各种不好用的地方，我没有看见它去考虑一些细节（而且都是些挺可行、成熟的方案）或者沟通交流（讨论区还有帖子没被回复，群里回复像且仅像是答疑）。既然无法改变对象，那就自己动手，这也是本插件诞生的原因。



## 原理



非常非常非常没有难度，看两天代码照着模板套你也可以做。



-   预览图片：直接注入js脚本从页面获取作业真实下载链接，如果是图片就直接用`<canvas>...</canvas>`嵌入到网页绘制而不必单独下载，并且可以单击旋转图片。如果不是图片，就转换为真实下载链接而不是`javascript:void(0);`（好像并没有什么卵用，你可能需要"一键下载本页"这种功能，但把作业拆成多份pdf的学生估计百年一遇......）。



-   放开下载：直接注入js脚本从页面修改课件可下载的属性。



## 安装方式



强烈推荐去商店下载，这样就不会有开发者模式的弹窗了。



### 插件商店下载



> 支持Chrome和Chromium Edge (新版Edge)，但是要科学地去上网。



1.  前往[教学立方辅助工具](https://chrome.google.com/webstore/detail/%E6%95%99%E5%AD%A6%E7%AB%8B%E6%96%B9%E8%BE%85%E5%8A%A9%E5%B7%A5%E5%85%B7/dpcoadobjphddblobamffijbelbkidga)；



2.  安装，结束。



### 加载压缩包方式



> 不是很旧的版本大概率都可以用。



1.  如果会使用git，使用`clone`到本地；如果不会使用git，选`Clone or download->Download ZIP`，将下载的`.zip`压缩包，解压成文件夹



![file](images/image-1586601362953.png)



2.  打开Chrome或Chromium

    Edge浏览器，Chrome输入`chrome://extensions`，Edge输入`edge://extensions`



3.  打开"开发人员模式"，chrome浏览器在页面右上角，Edge浏览器在页面左下角



4.  Chrome点击"加载已解压的扩展程序"（左上角），Edge点击"加载解压缩的扩展"（右上角），然后选中本地的仓库文件夹



## 使用



### 通用



-   **开启背景模式**：（Experimental）开启后，无需点击插件图标，网页加载完毕后自动应用功能。图片较大或网页加载策略特殊时可能会失效，大概率和网络加载速度有关，建议一般还是使用点击模式。



> **👍点击模式**：推荐模式，沿袭了最初的插件版本。打开教学立方作业批改页面或课件列表，此时插件显示"Click"，点击插件图标。

>

> **🧪背景模式**：此为懒人实验性功能，。打开教学立方作业批改页面或课件列表，此时插件显示"On"，无需做任何动作。（但因为其不稳定性经常需要刷新就是了=。=）



-   **隐藏客服按钮**：开启后，将隐藏界面上悬浮客服按钮的遮挡



### 老师/助教功能



目前功能有：



-   **预览图片附件**：直接预览格式为`.png`/`.jpg`/`.jpeg`格式的图片附件



-   **点击预览的图片**：左键单击图片（无论是附件预览还是原先插入的），可以直接旋转



-   **优化"评阅"按钮位置**：将"评阅"按钮移动至视野下方随页面浮动，任何时候你都可以点击"评阅"而无需滚到最底下或最上方



-   **分散评阅**：为每个图片下方添加笔记框，自动汇总到评阅；当优化评阅按钮位置开启时，可以额外增加一个浮动笔记框，适合长图包含多个作业题时随手记录批改情况



-   **评阅后缀**：在总评后面添加一段类似个人签名的文字，非常适合用于多人批改分工时标记批改人



### 学生



目前功能有：



-   **一键复制下载链接**：~~显示课件真实url下载链接，可配合

    *DownThemAll!* 等批量下载工具使用~~

    一键复制本页可下载的课件的链接，可粘贴到迅雷等下载器直接下载。



## 已知问题



-   由于本人能力有限只能暂时解决图片问题（pdf和word文档基本都是一个文档其实也不太妨碍）



-   实际测试中，极个别图片显示不正常，目前不知道原因，但绝大多数可以用



-   ~~批改作业时，由于教学立方的载入模式的问题，点击"下一个"可能没有用，目前只有两个临时方案。**方案①**：不正常就刷新；**方案②**：从作业列表里点击"评阅"。~~

    此问题已经在版本`v2.0.4`中修复。



-   少数图片显示不正常或无法点击旋转，尝试刷新页面



## 欢迎改进



非常非常非常欢迎有大佬看见感兴趣可以改进的，特别是文件预览因为url含有验证遭遇到不小麻烦，暂时没办法解决。当然最好的办法是官方技术能抽个小空来改造，这样这个插件从此就用不上了......



## 更新日志



### v1.1



-   更名为教学立方辅助工具



-   仿照原来的方式，增加了一键显示所有下载的功能



-   吐槽：实现方式过于简单，这变量作用范围到底算bug还是算feature？



### v1.2



-   重新整理了下其实基本已经全是自己写的内容了，所以重新做了许可



-   对于改作业而言，增加了将"评阅"移到页面底部，看完作业直接评阅无需上翻



-   增强了图片预览功能，在开启预览之后点击图片可以直接旋转图片（无论是原先就有的还是附件预览）



-   添加了记录输入框，改小题的时候可以添加笔记，最后在评阅时汇总



### v1.3



-   将课件的下载链接替换为真实下载地址，推荐结合 *DownThemAll!*

    插件或类似工具能够实现批量下载



-   修复了课件列表切下一页后"下载"消失的问题（是的，我用了Timer）



### v1.x (x>3)



-   增加了很多bug



------------------------------------------------------------------------



### v2.0.1 (重大更新)



-   拆分重写了原先的各个模块



-   允许多个自定义功能



-   分为"点击"和"背景"模式



-   采用新的版本号



-   测试鸣谢：\@YoungMan



### v2.0.2



-   修正了文件下载跳两次的小问题



-   更改了LOGO\~



### v2.0.3



-   修改了课件链接显示机制，默认是不需要开启的，除非你想批量下载



-   修正了点击重复插入脚本的BUG



### v2.1.0（功能增强，推荐更新）



-   修改了评阅位置优化，现在无论如何滚动页面都可以看见"评阅"了



-   添加一个浮动评阅框（当评阅位置优化开启时可以使用），遇到批改作业图片较长时直接随手记



-   显著减少了批改页面点击"下一个"后无法使用插件必须刷新的BUG



-   显示所有下载链接后可以一键复制所有下载链接粘贴到下载工具内，不需要额外装插件



-   对功能描述进行了一些修改



### v2.1.1



-   优化了课件下载的机制：不勾选一键复制的时候，默认不会替换课件下载链接以及显示复制按钮，完全放弃与批量下载插件结合使用的方式
