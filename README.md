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