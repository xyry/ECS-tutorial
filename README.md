# 服务器使用说明

**服务器IP地址一定一定不要泄露**

用户名和密码找我要，每个用户的密码每个月都需要更换一次，如果我忘记了，请主动找我更换密码，为了服务器安全着想。

1. 数据集统一下载到/home/data

2. 工具类的安装包下载到 /home/tools，工具安装到自己的主目录下

3. 每个用户自己安装conda，安装包在/home/tools/miniconda下，安装过程一路默认即可，初始化那个可以yes

4. 安装了两个多会话工具，screen 和 tmux，按照自己习惯使用

   > screen 窗口下不能使用lrzsz传文件，会有bug

5. 上下传输文件可以用xftp,lrzsz

6. 若遇到xshell连上主机没有反应，可以尝试删除会话，重新新建一个会话

## 下载的数据集 /home/data

1. pascal_voc 2012 

   > ```shell
   > http://host.robots.ox.ac.uk/pascal/VOC/voc2012/VOCtrainval_11-May-2012.tar
   > ```
   >
   > 解压完VOCdevkit，其中包含
   >
   > 1. Annotations
   > 2. ImageSets
   > 3. JPEGImages
   > 4. SegmentationClass
   > 5. SegmentationObject


## 工具及其使用方法

## Conda

1. 安装完之后

   > ```shell
   > vim ~/.bashrc
   > #在最后一行写
   > export PATH=/home/your_id/miniconda3/bin:$PATH
   > #保存
   > :wq更新配置source ~/.bashrc
   > #测试conda是否安装完成 
   > conda list
   > 
   > # conda安装慢可以手动添加channel
   > conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
   > conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
   > conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
   > # 显示安装的频道
   > conda config --set show_channel_urls yes 
   > # 查看已经添加的channels
   > conda config --get channels
   > # 已添加的channel在哪里查看
   > vim ~/.condarc
   > ```

   


## Tmux(已安装)

功能：terminal multiplexer

详细的指令可以看这个网站 https://www.ruanyifeng.com/blog/2019/10/tmux.html ，tmux比较有意思的还是划分窗格，感兴趣可以学一下。

下面列出比较常用的一些。

新建一个指定名称的会话

> ```bash
> $ tmux new -s <session-name>
> ```

在 Tmux 窗口中，按下`Ctrl+b d`或者输入`tmux detach`命令，就会将当前会话与窗口分离。

> ```bash
> $ tmux detach
> ```

上面命令执行后，就会退出当前 Tmux 窗口，但是会话和里面的进程仍然在后台运行。

`tmux ls`命令可以查看当前所有的 Tmux 会话。

> ```bash
> $ tmux ls
> # or
> $ tmux list-session
> ```

`tmux attach`命令用于重新接入某个已存在的会话。

> ```bash
> # 使用会话编号
> $ tmux attach -t 0
> 
> # 使用会话名称
> $ tmux attach -t <session-name>
> 
> ```

`tmux kill-session`命令用于杀死某个会话。

> ```bash
> # 使用会话编号
> $ tmux kill-session -t 0
> 
> # 使用会话名称
> $ tmux kill-session -t <session-name>
> ```

### proxychains（未安装）

暂时不考虑😀，等以后如果有必要，实验室集资买一个挂服务器上

使用wget 或者git clone速度很慢，在指令前面加上proxychains4，conda需要自己手动添加清华源

### xftp(推荐)

功能：上传下载文件

### lrzsz

功能：上传下载文件

sz：将选定的文件发送（send）到本地机器
rz：运行该命令会弹出一个文件选择窗口，从本地选择文件上传到服务器(receive) 

注意，假如使用sz指令下载某个文件，文件里的文件是无法下载的，建议使用xftp传输文件。

### tree

功能：树形展开文件夹

``` 
(base) lll:~/cpp-export$ tree -L 1
.
├── CMakeLists.txt
├── example-app.cpp
├── libtorch
└── libtorch-cxx11-abi-shared-with-deps-1.4.0.zip


```

### CUDA及cudnn版本

cuda 版本 

```bash
cat /usr/local/cuda/version.txt
```

cudnn 版本 

```bash
cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
```

