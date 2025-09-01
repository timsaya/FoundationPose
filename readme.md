https://github.com/wualbert/FoundationPose


FoundationPose for RTX 5090

```

conda create -n foundationpose python=3.10

conda activate foundationpose

conda install conda-forge::eigen=3.4.0

# edit bundlesdf/mycuda/setup.py
# add eigen to include_dirs
# example     include_dirs=[ "/usr/local/include/eigen3","/usr/include/eigen3","/home/test/miniconda3/envs/foundationpose/include/eigen3"],


# edit requirements.txt . Keep the relevant versions that are compatible with RTX5090
# If you don't know what torch==2.8.0+cu129 means, open https://download.pytorch.org/whl/cu129 and search for the version you need. Or ask gpt.

# then
python -m pip install -r requirements.txt


# Install NVDiffRast
python -m pip install --quiet --no-cache-dir git+https://github.com/NVlabs/nvdiffrast.git


# PyTorch3D
pip install --extra-index-url https://miropsota.github.io/torch_packages_builder pytorch3d==0.7.8+pt2.8.0cu129


# install boost
conda install -c conda-forge boost


# Build extensions , replace your path .
export CMAKE_PREFIX_PATH=$CMAKE_PREFIX_PATH:~/miniconda3/envs/foundationpose/lib/python3.10/site-packages/pybind11/share/cmake/pybind11:~/miniconda3/envs/foundationpose/include
bash build_all_conda.sh