本文将讲解： 
如何从零开始学写Appinventor拓展（Appinventor extensions）

转载自 ColinTree At aix.colintree.cn
自(2016年)6月15号Appinventor开放更新NB149之后，App inventor引进了一个自由度非常高的内容：Extension（拓展组件）Appinventor 规定在App inventor本身的基础上，可以加入一些辅助性的不可视组件，但是权限放的相当的开！ 
于是乎，很多人都开始感兴趣，但是却不知如何下手写 
在本人的再三研究之后，总结了一系列的教程，将一直在这个帖子更新 

本文首发于[App inventor2百科网论坛](http://www.yzzyz.cn/bsb/) 以及 [作者的个人网站](aix.colintree.cn)

1.准备 

   1.1下载 
写Appinventor拓展文件(.aix)需要的工具有：

   1. Git 
Git是一个分布式版本控制软件，这里我们将用他来下载appinventor的源代码以及执行编译指令 
下载地址：[Git](https://git-scm.com/downloads)

   2. Ant 
Apache Ant，是一个将软件编译、测试、部署等步骤联系在一起加以自动化的一个工具，大多用于Java环境中的软件开发。 
Appinventor已经将他的源码编译过程全部浓缩到一个指令文件里，只需要我们使用Ant将其执行即可 
下载地址：[Apache Ant](https://ant.apache.org/bindownload.cgi)

   3. Google app engine 
事实上，在这里GAE客户端是一个备用选项，GAE客户端可以将Ant编译Appinventor生成的结果本地运行。这个是在官方文档里建议使用的，但是就个人来说，作者我并没有用这个方法，而是直接生成aix然后在网页上一次次的调试。 
更何况，国内Google还是不稳定的，所以本文还是不讲解了

   4. Java 
不意外的，写Java代码还得请Java本人。 
作者在测试的时候，发现最新的Java8似乎并不能用……所以我们要卸载所有Java8的Jre或者Jdk，然后安装最新的Java7版本。 
下载地址： [Jre](http://www.oracle.com/technetwork/cn/java/javase/downloads/jre7-downloads-1880261.html)   [JDK](http://www.oracle.com/technetwork/cn/java/javase/downloads/jdk7-downloads-1880260.html)

   5. Jedit 
Jedit是作者推荐用来编辑Java源代码的一个IDE 
下载地址：[jedit](http://www.jedit.org/index.php?page=download)

1.2 安装、配置（按顺序） 
1. Git 
双击安装下载好的安装包 
其中建议如图选择：（添加快捷方式到桌面） 
![image](http://extensions.sinacloud.net/ArticlePics/HowToWriteAIX/2-image002.jpg "pic")
其他选项保持默认

2. Java 
按默认路径安装Jre 
按默认路径安装Jdk 
右击“计算机”，点击“属性”，点击弹出界面的左部分的“高级系统设置”，选择“高级”选项卡，点击下部的“环境变量” 
在“系统变量”中，设置属性JAVA_HOME、CLASSPATH、Path（不区分大小写）,若已存在则点击“编辑”，不存在则点击“新建” 
1)	JAVA_HOME指明JDK安装路径，就是刚才安装时所选择的路径/Java/jdk1.7.0_79，此路径下包括lib，bin，jre等文件夹 
2)	Path使得系统可以在任何路径下识别java命令，这里，要注意下，path应该是本来就存在的，就不要新建了，找到path，点击“编辑”；在值的最前面加上下面的语句即可。如果覆盖了path变量，将导致的cmd下有些基本的命令会找不到。 
```
%JAVA_HOME%/bin;%JAVA_HOME%/jre/bin;
```

3)	CLASSPATH为java加载类(class or lib)路径，只有类在classpath中，java命令才能识别，设为： 



