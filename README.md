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



## Errors & Solve



