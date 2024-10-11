# 3D Gaussian Splatting for Real-Time Radiance Field Rendering with C Kernel primarily on the CPU

This repository provides a C implementation of the 3D Gaussian Splatting for Real-Time Radiance Field Rendering, focusing on running the kernel computations primarily on the CPU. The only change made is rewriting the core forward computation of the diff-gaussian-rasterization in C for CPU rendering (only depending on libc).

```shell
# clone
git clone <url> --recursive

# env
conda env create -f environment.yml

# 
pip install -e ./diff-gaussian-rasterization
pip install -e ./submodules/simple-knn

# download models and db
wget https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/datasets/pretrained/models.zip
uznip models.zip
wget https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/datasets/input/tandt_db.zip
unzip tandt_db.zip "db/*" -d .

# render
python render.py -m models/drjohnson/ -s db/drjohnson/ --data_device cpu --resolution 100
python metrics.py -m models/drjohnson/
```
