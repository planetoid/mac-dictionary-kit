sdconv -- stardict 到 Dictionary 格式转换器 0.3
===============================================

sdconv 是一个将 stardict 格式 [1] 词典 [2] 转换为 Mac OS X 10.5 的 
Dictionary 2.0 [3] 词典格式的转换工具。

系统需求
--------

- Mac OS X 10.5 "Leopard"

最近更新
--------

* 支持用 Python 脚本定义转换函数 (transform)
* 支持 -d 参数选择调试模式 (只输出开头一部分词典项)
* 重组代码，libmdk C++ 库可以用于其他应用程序

安装
----

下载 sdconv-0.3.tar.bz2 压缩包后，将其解压到如 ~/ 这样的目录下: 

    $ tar -jxf sdconv-0.3.tar.bz2 -C ~/
    $ export CONVERTER_PATH=~/sdconv-0.3

在下面我们会使用环境变量 $CONVERTER_PATH 表示用于执行转换脚本的路径。

使用
----

1. 从 [2] 下载你需要的词典，例如我们需要 stardict-cedict-gb-2.4.2.tar.bz2: 

    $ cd ~/Downloads
    $ wget http://jaist.dl.sourceforge.net/sourceforge/stardict/stardict-cedict-gb-2.4.2.tar.bz2

2. 任意选择一个你有权限写入并有足够空间的目录，作为当前的工作目录。
假设原始的词典文件是 10 MB，那么你应该预留超过 500 MB 的空余磁盘空
间。进入此工作目录:

    $ cd ~/Documents/Dictionaries

然后执行:

    $ $CONVERTER_PATH/convert ~/Downloads/stardict-cedict-gb-2.4.2.tar.bz2

3. 如果没有看到任何错误信息，这样就大功告成了。一个叫做 cedict-gb.dictionary 
的词典 bundle 会出现在你的 ~/Library/Dictionaries 目录下。启动 
Dictionary.app 看看这个词典是否可用。

4. 如果遇到了什么问题，请联系维护者: <gzjjgod@gmail.com>。

定制
----

目前我们只提供了很见的的定制功能，通过 $CONVERTER_PATH 目录下的 templates/ 
模板实现，你可以修改 Dictionary.css 来定制生成词典的外观。如果你需要更多的
定制功能，比如必须修改 HTML 标记才能实现，请使用 -s 参数选择一个 Python 脚
本进行输出。

编译
----

编译 sdconv 需要安装 Xcode Tools 3.0+。在 $CONVERTER_PATH 下，输入

    $ cd src && make

这样就可以生成所需的 bin/converter 和 lib/libmdk.dylib 程序，你可以通
过 $CONVERTER_PATH/convert 这个 Python 脚本来调用它。

[1] https://stardict.svn.sourceforge.net/svnroot/stardict/trunk/doc/StarDictFileFormat
[2] http://stardict.sourceforge.net/Dictionaries.php
[3] http://www.appleinsider.com/articles/07/10/04/road_to_mac_os_x_leopard_dictionary_2_0.html

