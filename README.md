[comment]: <> 

<!-- PROJECT LOGO -->

<p align="center">

  <h1 align="center"> DUSt3R: Geometric 3D Vision Made Easy
  </h1>

[comment]: <> (  <h2 align="center">PAPER</h2>)
  <h3 align="center">
  <a href="https://kwanwaipang.github.io/File/Blogs/Poster/MASt3R-SLAM.html">Blog</a> 
  | <a href="https://github.com/naver/dust3r">Original Github Page</a>
  </h3>
  <div align="justify">
  </div>

<br>

* 安装步骤（step-by-setp，看似配置过程没有太多依赖问题）
~~~
conda create -n dust3r python=3.11 cmake=3.14.0
conda activate dust3r 
# conda install pytorch torchvision pytorch-cuda=12.1 -c pytorch -c nvidia  # use the correct version of cuda for your system
# conda install pytorch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2 pytorch-cuda=11.7 -c pytorch -c nvidia
conda remove --name dust3r --all


pip install -r requirements.txt
# Optional: you can also install additional packages to:
# - add support for HEIC images
# - add pyrender, used to render depthmap in some datasets preprocessing
# - add required packages for visloc.py

pip install -r requirements_optional.txt


# DUST3R relies on RoPE positional embeddings for which you can compile some cuda kernels for faster runtime.
cd croco/models/curope/
python setup.py build_ext --inplace
cd ../../../

~~~

* 下载权重
~~~
mkdir -p checkpoints/
wget https://download.europe.naverlabs.com/ComputerVision/DUSt3R/DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth -P checkpoints/
~~~

* 运行测试（注意采用的是网页UI）
~~~
cd /home/gwp/dust3r/
conda activate dust3r 

CUDA_VISIBLE_DEVICES=0 python3 demo.py --weights checkpoints/DUSt3R_ViTLarge_BaseDecoder_512_linear.pth

http://localhost:7860/

python3 demo.py --model_name DUSt3R_ViTLarge_BaseDecoder_512_dpt

# Use --weights to load a checkpoint from a local file, eg --weights checkpoints/DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth
# Use --image_size to select the correct resolution for the selected checkpoint. 512 (default) or 224
# Use --local_network to make it accessible on the local network, or --server_name to specify the url manually
# Use --server_port to change the port, by default it will search for an available port starting at 7860
# Use --device to use a different device, by default it's "cuda"
~~~

* 注意可能出现的bug比如'''RuntimeError: Numpy is not available'''大几率是numpy的问题~
~~~
pip install numpy==1.24.1
~~~

#测试效果

<div align="center">
  <img src="./assets/微信截图_20241225224243.png" width="80%" />
  <img src="./assets/微信截图_20241225224321.png" width="80%" />
  <img src="./assets/微信截图_20241225224331.png" width="80%" />
</div>
