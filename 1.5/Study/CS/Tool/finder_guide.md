# Finder 实用技巧

<!-- MarkdownTOC -->

- 在 Finder 窗口显示更多信息
- 让文件扩展名始终显示
- 使 Finder 默认显示自定义目录
- 在侧边栏显示用户目录
- 在 Finder 标题栏显示完整路径
- 始终显示用户「资料库」
- 显示 Finder 隐藏文件
- 显示文件（夹）的信息
- 你必须知道的 3 个快捷键
    - CMD－Z：撤消文件的复制、移动或删除操作（CMD－Z）
    - Return（回车）键：重命名文件/文件夹
    - Space（空格）键：即时预览
    - 导航操作
- 文件批量重命名
- 合并／拆分多窗口
    - 合并多窗口
    - 拆分多窗口
- 直接从选中项目新建文件夹
- 快速浏览某一标签的所有文件
- 参考资料

<!-- /MarkdownTOC -->


## 在 Finder 窗口显示更多信息



打开任意 Finder 窗口。前往并打开「显示」－「显示路径栏」、「显示」－「显示状态栏」和「显示」－「显示预览」三项。

路径栏通常是从磁盘分区开始的，没改过名字的就叫做「Macintosh HD」，接下来是「用户」，可是路径信息的这两个项目几乎没什么作用，我们需要看的一般都是从个人账户开始后面的路径。下面我们就来尝试删除这两个路径选项：

打开终端，输入以下命令：

    defaults write com.apple.finder PathBarRootAtHome -bool TRUE;killall Finder

回车后 Finder 会重启一下，改变即可见。

恢复默认：打开终端，输入如下代码并回车就可以恢复原样：

    defaults delete com.apple.finder PathBarRootAtHome;killall Finder

## 让文件扩展名始终显示

当你看到一个文件但是不知道它的格式的时候，会不会困惑？每次都要去简介页面查看文件是 .jpg 还是 .png 是不是很繁琐？哦，还有 CMD－i 快捷键？但是这些都比默认就显示来得慢。

打开 Finder 偏好设置，选中「高级」标签，然后在「始终显示文件扩展名」前面打勾即可。

## 使 Finder 默认显示自定义目录

「我的所有文件」是一个非常实用的功能。但是这对于那些需要按照目录来显示文件的用户来说，每次都需要进行一次额外的操作才能打开用户目录或者其他文件夹。让我们取消默认显示「我的所有文件」功能：

打开 Finder 偏好设置，选中「通用」标签，然后在「开启新 Finder 窗口时打开」项下选择你喜欢的目录即可。

## 在侧边栏显示用户目录

在 Mac 系统中，绝大多数用户文件，例如音乐、照片等都存储在用户目录下，所以在 Finder 侧边栏一直显示用户目录的内容是一个好主意。设置起来同样很简单：

打开 Finder 偏好设置，选中「边栏」标签，然后记得勾选你的用户名。

## 在 Finder 标题栏显示完整路径

众所周知 Finder 是不显示路径的，你进入某个文件夹只会显示当前文件夹的名字而已。虽然你可以通过上文中的方法将路径栏调出来，但是这样也增加了 Finder 窗口的高度，对小屏幕机器尤为不利。那么，让我们更进一步，将 Finder 的完整路径显示在标题栏如何？

打开终端，输入以下命令并回车：

    defaults write com.apple.finder _FXShowPosixPathInTitle -bool YES

然后把 Finder 窗口关了再打开，你会发现路径栏变样子了：

其实呢，对着路径最左边的小图标点右键，就能快速访问路径中的任意一层：

恢复

    defaults write com.apple.finder _FXShowPosixPathInTitle -bool NO

## 始终显示用户「资料库」

用户资料库是用来储存配置文件、缓存和用户数据的目录（路径：\~/Library/），由于 OS X 设置了系统文件保护，资料库在 Finder 中被设置为默认不显示。然而，通过终端执行一个简单的命令，就可以让它始终显示了。

打开终端，运行以下命令：

    chflags nohidden ~/Library/

回车即可。

## 显示 Finder 隐藏文件

喜欢捣鼓隐藏文件的用户看过来吧，我们可以让 Finder 始终显示隐藏文件或文件夹。

打开「终端」应用程序输入如下命令：

    defaults write com.apple.finder AppleShowAllFiles -boolean true ; killall Finder

回车即可。现在你将会在 Finder 中看到隐藏的文件和文件夹了。

恢复默认：将上述命令换成下面这条即可。

    defaults write com.apple.finder AppleShowAllFiles -boolean false ; killall Finder

## 显示文件（夹）的信息

Finder 可以告诉你一些关于文件和文件夹的非常实用的信息，比如选中的文件夹内有多少个文件、照片的分辨率（这个笔者最喜欢）等等。对于笔者这种重度截图党来说，这几乎是一个「必选」的设置。

在桌面点击鼠标右键，选择「查看显示选项」，选中「显示项目简介」项，现在看看，你的文件、文件夹有什么变化？

## 你必须知道的 3 个快捷键

### CMD－Z：撤消文件的复制、移动或删除操作（CMD－Z）

CMD－Z 是一个深度整合的快捷键，你可以简单理解为「撤消」操作，无论是撤销文本输入或是撤销文件删除操作。按一下 CMD－Z，就会返回到上一状态。尤其是删除文件了，一次就可以复位，非常方便。

已经连续删除了好几个文件？移动了好几次文件？没有关系，你只需多按几次 CMD－Z，直到你发现完全恢复了以前的样子为止。

▲ 注：若是重启了 Finder，该快捷键就没法了。

### Return（回车）键：重命名文件/文件夹

重命名文件/文件夹的最简单方法是在选择该项目后，按一下 Return 键（回车键）。这将即刻选中文件/文件夹的名称并呈现可编辑的状态。立刻开始输入新名称吧​​。完成命名了？再敲一次回车键即可。简单方便。

当然这不是 OS X 里重命名文件或文件夹的唯一方式，你还可以使用标题栏，或是命令行，或是使用鼠标点击文件名来实现。但是，哪个快？

### Space（空格）键：即时预览

Finder 内置了最为 handy 的即时预览功能（我个人最喜欢的 Finder 功能之一），一旦你会了，简直是离不开它。在 Finder 中选择任何一个项目，按下空格键。这将立即打开一个特殊窗口：Pdf 也好，音乐也好，视频也好，几乎什么格式都可以立即实时预览。再按一下空格键，就可立即关闭这个预览窗口。

### 导航操作

除了“CMD+上”和“CMD+下”来“退出一层”和“进入一层/打开”之外，“CMD+[”和“CMD+]”来“前进”“后退”也是一定要学会的。

## 文件批量重命名

在 OS X Yosemite 发布之前，对 Finder 中的文件进行重命名操作可谓是不怎么方便，也许你会想到使用「Automator」应用程序，或者是借助第三方（多数为收费的）应用程序。但是感谢 Yosemite，在 Finder 窗口内直接就可以进行批量重命名了。

第一步：打开 Finder 窗口，找到要重命名的文件。

第二步：按住 Shift 键单击选择多个文件。

第三步：右键单击弹出选项菜单，选择「重命名 XX 项目」。

第四步：选择重命名的类型后，点击重命名按钮。

重命名操作非常灵活：你可以使用替换文本命令，或者在文件名称之前或之后添加文本，或者直接完全重新进行重新命名（还可以设定添加递增序号等）。

如果你对更改结果不满意，使用 Command+Z 组合快捷键。

## 合并／拆分多窗口

如果你工作的时候需要参考很多的文档，你可能会打开多个 Finder 窗口，有时候桌面会显得凌乱不堪；有时候你在 Finder 窗口内打开了多个选项卡，切换起来不方便，也许你也会想将它们拆分开来。

### 合并多窗口

直接在菜单栏选择「窗口」－「合并所有窗口」项即可。

### 拆分多窗口

在菜单栏选择「窗口」－「将标签页移到新窗口」。

## 直接从选中项目新建文件夹

从其他地方迁移了多个零散文件，想将它们放入一个文件夹的话。平时你可能会首先新建一个文件夹，再选中所有的文件，然后将它们再移动进去。然而在 OS X，你可以不用这么麻烦。

第一步：选中所有需要放入文件夹的文件。

第二步：在任一文件上右键单击，选择「从所选项新建文件夹」选项。

## 快速浏览某一标签的所有文件

假设你已经有很多给很多文件打上了标签，你可以在 Finder 窗口左栏「个人收藏」选项下面找到它们。你可以点击某一个标签来在右侧的 Finder 窗口中浏览匹配的文件。

但是笔者还有更快的方法。为了更快地找到标记的文件，你可以简单地把 Finder 侧边栏下的标签拖到 Dock 中，无论你何时想浏览匹配的文件，只需要一次点击即可。

点击 Dock 中的标签，然后点击最上面的箭头图标（显示更多），即可将它们在一个 Finder 窗口中打开。

## 参考资料

[少数派1](http://sspai.com/27403)

[少数派2](http://sspai.com/28385)
