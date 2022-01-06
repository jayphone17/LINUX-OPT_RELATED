# Linux配置操作大全





## Conda相关

查看conda环境

```
conda info -e 
conda env list
```

创建conda新环境：

```
conda create -n xxx python=3.7 -y
```

删除conda环境：

```csharp
conda remove -n xxx --all
```

重命名conda环境：

```bash
conda create --name B --clone A
conda remove --name A --all
```

激活/进入环境：

```
conda activate xxx
```

conda查看所有源：

```
conda config --show-sources
```

conda删除所有源

```
conda config --remove-key channels
```

2021conda最新镜像源

南邮

```
channels:
  - https://mirrors.njupt.edu.cn/anaconda/cloud/pytorch/
  - https://mirrors.njupt.edu.cn/anaconda/cloud/menpo/
  - https://mirrors.njupt.edu.cn/anaconda/cloud/bioconda/
  - https://mirrors.njupt.edu.cn/anaconda/cloud/msys2/
  - https://mirrors.njupt.edu.cn/anaconda/cloud/conda-forge/
  - https://mirrors.njupt.edu.cn/anaconda/pkgs/main/
  - https://mirrors.njupt.edu.cn/anaconda/pkgs/free/
```

北外

```
conda config --add channels https://mirrors.bfsu.edu.cn/anaconda/pkgs/main
conda config --add channels https://mirrors.bfsu.edu.cn/anaconda/pkgs/free
```

清华

```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
```

中科大

```
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/bioconda/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/menpo/
```

清理conda未使用缓存：

```
conda clean -p
conda clean -a
```



## Pytorch相关

安装pytorch：

```
conda install pytorch torchvision -c pytorch
```

指定cuda版本安装pytorch：

```
conda install pytorch=xxx cudatoolkit=xxx torchvision=xxx -c pytorch
```

卸载Pytorch

```
conda uninstall pytorch
pip uninstall torch
```



## MMDetection相关

自动安装：

```
pip install openmim
or：
pip install -i https://pypi.douban.com/simple --trusted-host pypi.douban.com openmim

mim install mmdet
or：
mim install mmdetection -f https://github.com.cnpmjs.org/open-mmlab/mmdetection.git
```

手动/mccv-full安装：

```
pip install mmcv-full -f https://download.openmmlab.com/mmcv/dist/{cu_version}/{torch_version}/index.html
```

```
pip install mmdet
```

安装mmdet：

```
pip install mmdet
```

或者手动clone安装：

```
git clone https://github.com/open-mmlab/mmdetection.git
cd mmdetection
pip install -r requirements/build.txt
pip install -v -e .  # or "python setup.py develop"
```

mccv其他依赖包：

```
# for instaboost
pip install instaboostfast
# for panoptic segmentation
pip install git+https://github.com/cocodataset/panopticapi.git
# for LVIS dataset
pip install git+https://github.com/lvis-dataset/lvis-api.git
# for albumentations
pip install albumentations>=0.3.2 --no-binary imgaug,albumentations
```

Verification：

```
python demo/xxx.py demo/xxx.jpg configs/xxx（随便选一个，推荐faster_rcnn）/xxx.py checkpoints/xxx.pth
```

实例：

```
python demo/xxx.py demo/demo.jpg configs/faster_rcnn/faster_rcnn_r50_fpn_1x_coco.py checkpoints/faster_rcnn_r50_caffe_fpn_mstrain_1x_coco-5324cff8.pth
```



## 训练模型CUDA相关

查看当前显卡使用情况

```
nvidia-smi
```



## pip相关





## Brew相关





## Cmake相关

```
$ cd /刚刚/文件夹/的位置
$ mkdir build
$ cd build
$ cmake ..
$ make
```



# LabelMe相关

```
labelme  # 打开labelme软件

labelme xxx.jpg  # 指定图像文件
labelme xxx.jpg -O xxx.json  # 保存后关闭labelme
labelme xxx.jpg --nodata  # JSON文件不包含图像数据，而包含图像的相对路径
labelme xxx.jpg \
  --labels highland_6539_self_stick_notes,mead_index_cards,kong_air_dog_squeakair_tennis_ball  # 指定 label list

labelme data_annotated/  # 指定图像文件夹
labelme data_annotated/ --labels labels.txt  # 使用文件指定 label list
```



```
--flags： comma separated list of flags 或者 file containing flags
--labels：comma separated list of labels 或者 file containing labels
--nodata：stop storing image data to JSON file
--nosortlabels：stop sorting labels
--output：指定输出文件夹
```



```
1. labelme_draw_json：
   使用该命令可以快速查看JSON格式的标注。
2. labelme_json_to_dataset：
   使用该命令可以将JSON文件转为一组图像和标签文本文件。
3. labelme_draw_label_png：
   将label文本文件以图例的形式绘制到PNG格式的标签上，并显示出来。
```





## Errors & Solve

手动安装pycocotools：

直接使用pip安装

```
pip install pycocotools
```

显示：

```
Failed to build pycocotools
Installing collected packages: pycocotools
    Running setup.py install for pycocotools ... error
```

提示：

```
error: Microsoft Visual C++ 14.0 or greater is required. Get it with "Microsoft C++ Build Tools": https://visualstudio.microsoft.com/visual-cpp-build-tools/
```

原来pycocotools作者表示不支持windows
github上一位大佬制作了windows版本的：

```
https://github.com/philferriere/cocoapi
```

<img src="/pics\image-20220106191534448.png" alt="image-20220106191534448" style="zoom:50%;" />

并且需要Visual C++ 2015 build tools 或者以上

<img src="/pics\image-20220106191618625.png" alt="image-20220106191618625" style="zoom:50%;" />

并且选择默认选项

<img src="/pics\image-20220106191737895.png" alt="image-20220106191737895" style="zoom:50%;" />

由于官网Visual C++ 2015 build tools 离线安装的问题涉及到与开发编码有关

会提示包损失或者数据损失

但是看到有的人开全局梯子可以解决，but it didn't work for me

所以看到CSDN上有一个大佬把所有包收集好了，打包成ISO，直接下载然后exe安装就可以了

<img src="/pics\image-20220106191920947.png" alt="image-20220106191920947" style="zoom: 67%;" />

度盘：

```
链接：https://pan.baidu.com/s/19F4YurwwZ5A9WF5txzMZoQ 提取码：ka7q
```

安装完毕后：

```
pip install git+https://github.com/philferriere/cocoapi.git#subdirectory=PythonAPI
```

提示：

```
Collecting git+https://github.com/philferriere/cocoapi.git#subdirectory=PythonAPI
  Cloning https://github.com/philferriere/cocoapi.git to c:\users\jayphonelin\appdata\local\temp\pip-req-build-_q375vqo
  Running command git clone -q https://github.com/philferriere/cocoapi.git 'C:\Users\JayphoneLin\AppData\Local\Temp\pip-req-build-_q375vqo'
  Resolved https://github.com/philferriere/cocoapi.git to commit 2929bd2ef6b451054755dfd7ceb09278f935f7ad
Building wheels for collected packages: pycocotools
  Building wheel for pycocotools (setup.py) ... done
  Created wheel for pycocotools: filename=pycocotools-2.0-cp38-cp38-win_amd64.whl size=77094 sha256=3bfc70c456436da29848abb45ef49b2ec842426543f74a40bf85e61411b8b7f3
  Stored in directory: C:\Users\JayphoneLin\AppData\Local\Temp\pip-ephem-wheel-cache-ir1wzooi\wheels\bd\1c\0d\8c82e1b9bc855b82e1eb53eadea4459efe171d2daf5a222701
Successfully built pycocotools
Installing collected packages: pycocotools
Successfully installed pycocotools-2.0
```

