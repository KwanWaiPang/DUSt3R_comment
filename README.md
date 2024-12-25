[comment]: <> 

<!-- PROJECT LOGO -->

<p align="center">

  <h1 align="center"> DUSt3R: Geometric 3D Vision Made Easy
  </h1>

[comment]: <> (  <h2 align="center">PAPER</h2>)
  <h3 align="center">
  <a href="https://kwanwaipang.github.io/File/Blogs/Poster/paper_reading_MASt3R-SLAM.html#dust3r:-geometric-3d-vision-made-easy">Blog</a> 
  | <a href="https://github.com/naver/dust3r">Original Github Page</a>
  </h3>
  <div align="justify">
  </div>

<br>

* 安装步骤（step-by-setp，看似配置过程没有太多依赖问题）
~~~
conda create -n dust3r python=3.11 cmake=3.14.0
conda activate dust3r 
conda install pytorch torchvision pytorch-cuda=11.7 -c pytorch -c nvidia  # use the correct version of cuda for your system

pip install -r requirements.txt
# Optional: you can also install additional packages to:
# - add support for HEIC images
# - add pyrender, used to render depthmap in some datasets preprocessing
# - add required packages for visloc.py

pip install -r requirements_optional.txt
~~~

* 下载权重
~~~
mkdir -p checkpoints/
wget https://download.europe.naverlabs.com/ComputerVision/DUSt3R/DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth -P checkpoints/
~~~

* 运行测试（注意服务器中要借助MobaXterm进行可视化）
~~~
cd /home/gwp/dust3r/
conda activate dust3r 
python3 demo.py --model_name DUSt3R_ViTLarge_BaseDecoder_512_dpt

# Use --weights to load a checkpoint from a local file, eg --weights checkpoints/DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth
# Use --image_size to select the correct resolution for the selected checkpoint. 512 (default) or 224
# Use --local_network to make it accessible on the local network, or --server_name to specify the url manually
# Use --server_port to change the port, by default it will search for an available port starting at 7860
# Use --device to use a different device, by default it's "cuda"
~~~