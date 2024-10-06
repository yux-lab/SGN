following 原教程，修改. so 路径


requirements
```bash
yapf==0.40.1
setuptools==59.5.0
```

将 save_flag=False 改成 True
设置 pred 路径
CTRL + F ：modified by

存疑
`mmcv.dump(outputs['bbox_results'], args.out)` -> `mmcv.dump(outputs, args.out)`


## kitti api 可视化
follow: [GitHub - PRBonn/semantic-kitti-api: SemanticKITTI API for visualizing dataset, processing data, and evaluating results.](https://github.com/PRBonn/semantic-kitti-api?tab=readme-ov-file)

### conda 换源 
`vim ~/.condarc`
```bash
channels:
  - defaults
show_channel_urls: true
channel_alias: https://mirrors.tuna.tsinghua.edu.cn/anaconda
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/pro
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
```

### pip 换源
`vim ~/.pip/pip.conf`
```bash
[global] 
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
```

### kitti api 可视化
```bash
# 创建虚拟环境
conda create -n kitti_api python=3.9 -y

# 激活
conda activate kitti_api
```

```bash
# 将kitti-api拉到本地
git clone https://github.com/PRBonn/semantic-kitti-api.git

# 进入目录并安装相应环境
cd semantic-kitti-api/
pip install -r requirements.txt
pip install PyOpenGL==3.1.1a1

# 添加环境变量
vim ~/.bashrc 
# 将下行添加到.bashrc最后一行
export MESA_GL_VERSION_OVERRIDE=3.3
# 激活
source ~/.bashrc

# 激活后需要再次激活虚拟环境
conda activate kitti_api

# 运行脚本可视化
# 文件路径遵守kitti api中的readme
python visualize_voxels.py --sequence 08 --dataset /mnt/data2/mmdetection3d/SGN/sgn/

## ./visualize_voxels.py --sequence 00 --dataset /path/to/kitti/dataset/
```
