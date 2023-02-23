# Team-G for 《基于SSR开发仿掘金站点》

## 项目启动

1. fork cms 数据层仓库`branch thy`参照对应 `readme` 启动
2. nuxtjs-demo 启动

```
npm install
npm run dev
```

# 📋前言
 <font color=#000> 这篇文章是关于在vscode终端中创建<font bgcolor=#fbd4d0 color=#be191c>**nuxtjs项目**</font>的一些步骤，同时还包括了使用<font bgcolor=#fbd4d0 color=#be191c>**Git、GitHub**</font>的一些操作，以此文章作为笔记，仅供参考。（前提：已经安装nodejs、git）
 
>- <font color=#000>**关于nuxtjs、ssr、服务端渲染、nuxtjs项目结构等等相关知识点这篇文章就不多多介绍了，在后续的文章或笔记中也还会介绍这些内容（做笔记），接下来就直入主题吧！**
>
>- <font color=#000>**相关链接：**[nuxtjs官网](https://www.nuxtjs.cn/)

---
# 💻关于GitHub打开慢或无法打开的问题
 <font color=#000>说实话这个问题对于我来说，很玄学，平时用GitHub比较少，用gitee比较多，但是当我需要用到GitHub或者要长时间使用时，它就经常出现无法访问、链接超时的问题。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2e0bf92a3e9543ca9cca0824d8af37cb.png)
 <font color=#000>于是通过查找问题和资料查询，大多数方法都说是hosts文件添加上GitHub的ip地址就行了，接下来我们实操一下。

 1. 首先找到GitHub的ip地址，通过 [https://tool.lu/ip/](https://tool.lu/ip/) 这个在线工具获取。
![在这里插入图片描述](https://img-blog.csdnimg.cn/4bbc750069a6482998c63b53e43cbd8d.png)
 1. 然后复制这个地址，添加到hosts文件里面。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2c5f09dff87e4d069761b3b1897c6462.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/fe96dfc332004ac9ac99d1c9265353e7.png)
 1. 如果没有意外的话，GitHub就可以正常打开。

---
# 💻克隆GitHub的项目到本地
 <font color=#000>首先在GitHub上面创建一个项目，用于等等的克隆，这里不再过多的赘述详细步骤了，直接看图一步一步来。
![在这里插入图片描述](https://img-blog.csdnimg.cn/610dbb2e0d124f518bb0fef9fc4993e7.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/11719b126beb45b88458925f88403e11.png)
<font color=#000>然后在本地创建一个新的文件夹，然后鼠标右键这个文件选择git bush here。
![在这里插入图片描述](https://img-blog.csdnimg.cn/93379bfac55c4f82b031721e106bd25c.png)
<font color=#000>然后 git init 初始化项目，git clone...(你的仓库地址)来克隆项目。
![在这里插入图片描述](https://img-blog.csdnimg.cn/fbb07bf118174805a0fa97bb7341f3cf.png)
<font color=#000>git clone下面这个HTTPS的仓库地址。
![在这里插入图片描述](https://img-blog.csdnimg.cn/6a27d9aa2de94982b8ba8ab5880637c9.png)
 <font color=#000>补充：这个是经典的创建仓库指令。
```
git init 	//把这个目录变成Git可以管理的仓库
git add README.md 	//文件添加到仓库
git add . 	//不但可以跟单一文件，还可以跟通配符，更可以跟目录。一个点就把当前目录下所有未追踪的文件全部add了 
git commit -m "first commit" 	//把文件提交到仓库
git remote add origin git@github.com:wangjiax9/practice.git 	//关联远程仓库
git push -u origin master 	//把本地库的所有内容推送到远程库上
```
---
# 💻创建nuxtjs项目
 <font color=#000>克隆完仓库，我们就可以开始创建nuxtjs项目了，这里我选择的是在vscode终端来继续创建项目，这样可以直接指定好在哪个文件夹下了。（前提：已经安装好vue/cli）
## 🧩无法加载文件的报错问题
<font color=#000>**报错如下：**
vue : 无法加载文件 C:\Users\ghw\AppData\Roaming\npm\vue.ps1，因为在此系统上禁止运行脚本。有关详细信息，请参阅 https:/go.microsoft.com/fwlink/?LinkID=135170 中的 about_Execution_Policies。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2a69651cc6f047ddb492152f267a3dce.png)
<font color=#000>**解决方法：**
 1. 以管理员身份运行PowerShell
 2. 执行：get-ExecutionPolicy，回复Restricted，表示状态是禁止的
 3. 执行：set-ExecutionPolicy RemoteSigned
 4. 选择y
![在这里插入图片描述](https://img-blog.csdnimg.cn/314ea8e6fe4b4a2bb80b4da08da9d7d0.png)
## 🧩使用vue init nuxt/starter demo出现的问题
<font color=#000>上面说到，解决完无法加载文件的问题以后，我们就可以使用 vue init nuxt/starter xxx来创建nuxtjs项目了。但是紧接着出现了如下的问题。
![在这里插入图片描述](https://img-blog.csdnimg.cn/291722138f2c49e2a6ea5fe6d251fc85.png)
<font color=#000>输入 **vue init nuxt/starter demo** 后，没有开始创建项目，而是叫我跑一下 **npm i -g @vue/cli-init** 这段命令安装脚手架，按照这个步骤跑一下，安装完成后，出现几个==WARN==，先不给予理会，然后继续跑 **vue init nuxt/starter demo** 来创建项目。但是又没有开始创建项目，出现 <font color=red>**vue-cli · Failed to download repo nuxt/starter: connect ETIMEDOUT 20.205.243.166:443**</font> 这个错误。其中在网上看到有一种说法是，这个错误是因为 vue/cli 的版本所导致的创建失败。
<font color=#000>**解决方法：** [参考文章](https://blog.csdn.net/qq_42951499/article/details/118485218)

## 🧩另一种命令创建nuxtjs项目
1️⃣<font color=#000>使用 npx 
npm install -g npx
npx create-nuxt-app < project-name >
2️⃣<font color=#000>或者用 yarn 
npm install -g yarn
yarn create nuxt-app < project-name >

---
<font color=#000>这里我选择了使用yarn来创建，因为要先安装yarn，所以安装时间用了864.39s。
![在这里插入图片描述](https://img-blog.csdnimg.cn/323c90fd1e3640b8853de5393e8fac7e.png)
<font color=#000>然后我们来分析下创建时的一些选项，从上到下，依次是：

 1. 输入项目名称（这个名称不是项目文件的名称）
 2. 选择编程语言
 3. 选择包管理器
 4. 选择UI框架
 5. 选择 Nuxt.js 的模块
 6. 选择代码检查工具
 7. 选择单元测试框架
 8. 选择渲染模式
 9. 选择部署方式
 10. 选择开发工具
 11. 输入你的GitHub用户名
 12. 选择版本管理工具

<font color=#000>然后启动项目。
![在这里插入图片描述](https://img-blog.csdnimg.cn/13dd9ca66d0b49e8b60cb2125b65625f.png)
<font color=#000>然后点击运行 <font color=#4178b5>**http://localhost:3000**</font> 这个链接 。
![在这里插入图片描述](https://img-blog.csdnimg.cn/a7fb65c8447544e886af87b4c0c1a83f.png)
<font color=#000>运行成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/5f5a6fe5dce04a4a8332f741a858a4c4.png)

# 💻提交与同步数据到GitHub仓库
<font color=#000>创建完 nuxtjs 项目以后，我们可以把这些新建的数据提交到 GitHub 仓库上面，因为已经提交了，所以新建个 html 文件来演示一次提交与同步的过程。
![在这里插入图片描述](https://img-blog.csdnimg.cn/4923647f65554be8bdf8d2ff54f6b6f9.png)
<font color=#000>然后可以在 vscode 上面提交，也可以在 git bush 上面提交。
<font color=#000>在 vscode 上面提交如下。
![在这里插入图片描述](https://img-blog.csdnimg.cn/01cfdb57eb584c279f4ac89a1d4b1161.png)
<font color=#000>1️⃣在 git bush 上面提交如下。
<font color=#000>2️⃣注意有时候出现超时、同步失败的情况，**下图二是两种出现错误的情况**，多 push 几次就行了。（我一般在 vscode 上面同步都会超时，所以我都是在 git bush 上面 push）
![在这里插入图片描述](https://img-blog.csdnimg.cn/866dbfa68e02477eae832aef414b955c.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/42365955c6004db094b8e1fc613d4272.png)
<font color=#000>最后在 GitHub 仓库上面查看，显示了刚刚提交的内容，说明提交与同步成功了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/b75d3717065541d09bb3dd67fa3b65f4.png)
<font color=#000>涉及到的命令如下：

 1. 首先我是创建了一个新的 branch ，通过 git branch -M xxx 这条命令来创建，xxx 是指 branch 的名称 。
 2. 然后是把数据提交到仓库，通过 git commit -m "xxx" 这条命令来操作，xxx 是指提交时的备注消息。
 3. 最后是把克隆到本地的仓库推送、同步到远程的 GitHub 仓库上面，通过 git push -u origin xxx 这条命令来操作，xxx 是指你的 branch ，这里的 branch 是新创建的那个。
