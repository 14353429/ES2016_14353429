## 一、 DOL框架描述

DOL是一个能够支持应用并发调试的框架，由以下三个部分组成：

- 应用程序接口
- 功能仿真
- 匹对优化

## 二、 DOL配置过程

### 1. 安装和更新必要的环境：

```javascript
$  sudo apt-get update
$  sudo apt-get install ant
$  sudo apt-get installopenjdk-7-jdk
$  sudo apt-get install unzip
```

​	整个过程比较久需要等待。

### 2. 下载systemc-2.3.1.tgz和dol_ethz.zip

​	有两种方法:

​	一种是直接在Vmware里面直接下载：

```c
$  sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
$  sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
```

​	另一种方法是直接将文件拷贝进去。

​	我选择了下载的方式，很快就下载完成了。

### 3. 解压下载完的文件

​	新建一个dol的文件夹，然后执行：

​	 `$  unzip dol_ethz.zip -d dol`

​	注意下面这个命令不是解压到dol文件夹里。
​	 `$  tar -zxvf systemc-2.3.1.tgz `

### 4. 编译systemc

​	进入目录后，新建一个文件夹objdir，在里面运行configure（用于后面的编译）：
​	`$  ../configure CXX=g++ --disable-async-updates`
​	然后正式编译：
​	`$  sudo make install`
​	用pwd命令记下当前的工作路径，我的是：/home/just/systemc-2.3.1

### 5. 编译dol

​	进入dol文件夹后，修改build_zip.xml:
​	找到以下代码段：

```javascript
$  <property name="systemc.inc" value="YYY/include"/>
$  <property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>  
```

​	然后把YYY改成上面的记下的工作路径/home/just/systemc-2.3.1。
​	最后编译：`$  ant -f build_zip.xml all`

到此完成DOL配置，结果如图所示：

 ![1](https://github.com/14353429/ES2016_14353429/blob/master/image/1.png)

## 三、 实验感想

配置过程比较简单，没有遇到难题。

关于Markdown的编辑平台，我使用的是Typora软件。但是本人还是比较喜欢CTEX，在那里编辑的风格会更好一点。但是Markdown语言非常简单，上手很快。
