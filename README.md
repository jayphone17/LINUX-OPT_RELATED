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

激活/进入环境：

```
conda activate xxx
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



## MMDetection

自动安装：

```
pip install openmim
mim install mmdet
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



## Brew相关





## Cmake相关

```
$ cd /刚刚/文件夹/的位置
$ mkdir build
$ cd build
$ cmake ..
$ make
```



## Errors & Solve



