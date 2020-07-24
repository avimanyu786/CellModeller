CellModeller CuPy Branch
========================
Multicellular modelling framework, originally created by Tim Rudge, PJ Steiner, and Jim Haseloff, University of Cambridge

<img src="https://data.plantsci.cam.ac.uk/Haseloff/files/stacks-image-5b52112.png" alt="Cells" width="200px"/>

This project starts with an attempt to replace NumPy and Math implementations on the existing Biophysics module on CellModeller with CuPy, that is an implementation of a NumPy-compatible multi-dimensional array on both NVIDIA and AMD GPUs. The main goal here is to make use of CuPy's interoperability with CellModeller's existing and primary backend: PyOpenCL, to maximize GPU parallelization and reduce CPU dependency while simulating cell growth. As separate versions, PyOpenCL and OpenCL based data handling have also been modified for double precision. In both CuPy implementations (single and double precision), NumPy code has not been revised to CuPy where there is interdependence between NumPy and OpenCL. In another version, arrays used while moving/dividing cells and updating cell neighbours in the Biophysics module have been converted to Tensors via DLPack/Tensorflow.

### CellModeller Website: [cellmodeller.org](http://cellmodeller.org)
