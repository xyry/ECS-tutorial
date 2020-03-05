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

7. 使用wget 或者git clone速度很慢，在指令前面加上proxychains4，conda需要自己手动添加清华源

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

