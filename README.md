CellModeller CuPy Branch
========================
Multicellular modelling framework, originally created by Tim Rudge, PJ Steiner, and Jim Haseloff, University of Cambridge

<img src="https://data.plantsci.cam.ac.uk/Haseloff/files/stacks-image-5b52112.png" alt="Cells" width="200px"/>

This branch is an attempt to replace NumPy and Math implementations on the existing Biophysics module on CellModeller with CuPy, that is an implementation of a NumPy-compatible multi-dimensional array on both NVIDIA and AMD GPUs. The main goal here is to make use of CuPy's interoperability with CellModeller's existing and primary backend: PyOpenCL, to maximize GPU parallelization and reduce CPU dependency while simulating cell growth. As separate versions, PyOpenCL and OpenCL based data handling have also been modified for double precision. In both CuPy implementations (single and double precision), NumPy code has not been revised to CuPy where there is interdependence between NumPy and OpenCL. In another version, arrays used while moving/dividing cells and updating cell neighbours in the Biophysics module have been converted to Tensors via DLPack/Tensorflow. In future work, CuPy can also be implemented in the other modules of CellModeller.

## CuPy Installation

### Assuming CellModeller and CUDA 9.0 are already installed

Using Conda to install CuPy would lead to a wipe-out of both CellModeller and PyOpenCL. To install CuPy within an existing CellModeller environment without affecting the existing CellModeller installation, we have to use Pip to install it instead of Conda.

```
cd ~/cellmodeller
conda activate cellmodeller
pip2 install --upgrade pip
pip2 install --user cupy-cupy90
```

## Tensorflow Installation

### Assuming CellModeller and CUDA 9.0 are already installed
#### Activate CellModeller Conda environment:
```
cd ~/cellmodeller
conda activate cellmodeller

```
### Tensorflow version 0.6.0 satisfies NumPy 1.9.2 dependency that is essential for CellModeller
```
pip install https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.6.0-cp27-none-linux_x86_64.whl
cd /usr/local/cuda-9.0/targets/x86_64-linux/lib
```

### The following workaround enables using the existing CUDA 9.0 API:
```
sudo ln -s libcudart.so.9.0 libcudart.so.7.0
sudo ln -s libcublas.so.9.0 libcublas.so.7.0
```
Assuming cuDNN 7.3.1 has been installed via tarball
```
sudo ln -s libcudnn.so.7.3.1 libcudnn.so.6.5 
sudo ln -s libcufft.so.9.0 libcufft.so.7.0
sudo ln -s libcurand.so.9.0 libcurand.so.7.0
```
### Now tensorflow imports would be ready for use in CellModeller.

### CellModeller Website: [cellmodeller.org](http://cellmodeller.org)
