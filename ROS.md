## 配置ROS

### 一、 ROS

#### 1. ROS全称Robot operation system，用于机器人的一种后（次）操作系统。它提供类似操作系统所提供的功能，包含硬件抽象描述、底层驱动程序管理、共用功能的执行、程序间的消息传递、程序发行包管理，它也提供一些工具程序和库用于获取、建立、编写和运行多机整合的程序。

#### 2. ROS是一种分布式处理框架（又名Nodes）。这使可执行文件能被单独设计，并且在运行时松散耦合。这些过程可以封装到数据包（Packages）和堆栈（Stacks）中，以便于共享和分发。

#### 3. 主要特点

##### 1). 点对点设计

##### 2). 多语言支持

##### 3). 精简与集成

##### 4). 工具包丰富

##### 5). 免费且开元

### 二、 ROS配置

​	整个ROS的配置没遇到什么问题，都是照着打命令，但是要注意的是中间有一个是选择

``sudo apt-get install ros-jade-desktop-full``，这样的话下面分出来的小步骤是不用做的。最后一步就是

``sudo apt-get install python-rosinstall`` ，这里就是装一个ROS的命令行。网页上最后一步的话

``apt-get source ros-jade-laser-pipeline``，安装会遇到问题，可以忽略。

### 三、 安装cartographer

​	这里的话我一开始是顺着步骤配置，但是到了以下的最后步骤会出错：

```
# Build and install.
catkin_make_isolated --install --use-ninja
source install_isolated/setup.bash
```

​	然后点进去一个system requirement里面配置。这里好像就是上面的指令的一些具体步骤吧，顺着做下去咯。

```
# Install the required libraries that are available as debs.
sudo apt-get update
sudo apt-get install -y \
    cmake \
    g++ \
    git \
    google-mock \
    libboost-all-dev \
    libcairo2-dev \
    libeigen3-dev \
    libgflags-dev \
    libgoogle-glog-dev \
    liblua5.2-dev \
    libprotobuf-dev \
    libsuitesparse-dev \
    libwebp-dev \
    ninja-build \
    protobuf-compiler \
    python-sphinx
```

```
# Build and install Ceres.
git clone https://ceres-solver.googlesource.com/ceres-solver
cd ceres-solver
mkdir build
cd build
cmake .. -G Ninja
ninja
ninja test
sudo ninja install
```

​	这里有一个git clone命令，但是会出错，不知道为何在ubuntu里下载不了，然后自己下载之后放到ubuntu里面就好了。然后解压命令的话是tar -zxvf ceres-solver。

​	这里test成功：

 ![passTest](https://github.com/14353429/ES2016_14353429/blob/master/image/passTest.png)

​	然后接着

```
# Build and install Cartographer.
cd cartographer
mkdir build
cd build
cmake .. -G Ninja
ninja
ninja test
sudo ninja install
```

​	这里有一个cd cartographer，但是我们还没下载，是自己去一个github上面下载的：

​	``git clone https://github.com/googlecartographer/cartographer.git``

​	test成功：

 ![passTest2](https://github.com/14353429/ES2016_14353429/blob/master/image/passTest2.png)

​	但是上面那里的配置还是会出错，唉实在没办法了。

### 四、 实验感想

​	这次实验收获最多的就是看一堆英文...不是看见命令就要输进去的，还是要看懂这些命令是干什么用的。
