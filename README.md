# 服务器使用说明

1. 数据集统一下载到/home/data

2. 工具类的安装包下载到 /home/tools，工具安装到自己的主目录下

3. 每个用户自己安装conda，安装包在/home/tools/miniconda下，安装过程一路默认即可，初始化那个可以yes

   安装完之后

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

4. 安装了两个多会话工具，screen 和 tmux，按照自己习惯使用

   > screen 窗口下不能使用lrzsz传文件，会有bug

5. 上下传输文件可以用xftp

6. 若遇到xshell连上主机没有反应，可以尝试删除会话，重新新建一个会话

8. 服务器IP地址不要外传

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

2. cifar-100

   > 开源项目pytorch-cifar100项目用的数据集

3. voc12_aug

   > - DUnet

4. caffe-ilsvrc12

   >- GhostNet

## 工具及其使用方法

### proxychains

使用wget 或者git clone速度很慢，在指令前面加上proxychains4，conda需要自己手动添加清华源

### xftp(推荐)

上传下载文件

### lrzsz（未安装）

上传下载文件

### tree

树形展开文件夹

``` 
(base) ypl:~/cpp-export$ tree -L 1
.
├── CMakeLists.txt
├── example-app.cpp
├── libtorch
└── libtorch-cxx11-abi-shared-with-deps-1.4.0.zip


```

### CUDA及cudnn版本

CUDA10.2

cudnn7.6.5

### 将终端输出追加到文件

1. 考虑到模型一般会跑很久，我们没有办法一直在电脑前面盯着输出，所以可以将输出追加到指定文件，举例

```shell
touch record.txt
python train.py >> record.txt
```

缺点，有时候不成功

2. logger

直接看代码

```python
import logging
logging.basicConfig(level=logging.DEBUG,
                    filename='test.log',
                    filemode='a',
                    format='%(asctime)s - %(pathname)s[line:%(lineno)d] - %(levelname)s: %(message)s')
a=1
logger=logging.getLogger('test')
stream_handler=logging.StreamHandler()
logger.addHandler(stream_handler)
logger.debug(a+1)
```

