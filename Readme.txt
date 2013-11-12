Introduction
============

This is an implementation of t-SNE in CUDA, designed to run in Matlab. The document gives a brief description of how to install and use the CUDA implementation of t-SNE.

Laurens van der Maaten, 2010
University of California, San Diego


Installation instructions
=========================

Step 1
- Make sure you have a CUDA-enabled GPU. A list of CUDA-enabled GPUs is available from http://developer.nvidia.com/cuda-gpus

Step 2
- Download and install the CUDA Developer Drivers and the CUDA Toolkit. The software has been tested for CUDA 5.x. For earlier versions of CUDA, please see the original distribution of this code at http://homepage.tudelft.nl/19j49/t-SNE.html which has been tested for CUDA 3.x. Both the drivers and the toolkit are available from http://developer.nvidia.com

Step 3
- Add the directory that NVCC is located in to the PATH. On *nix systems, NVCC is typically located in /usr/local/cuda/bin or /usr/local/cuda-5.0/bin, and one can use SETENV or EXPORT to update the PATH (depending on the shell used). On Windows systems, the PATH can be set through the configuration screen (under Environment Variables).

Step 4
- Start MATLAB, and use the 'mexall' function to compile the code. The 'mexall' function has two input arguments that allow you to specify the location of the CUDA libraries and of the HELPER include file (helper_cuda.h). If no location is specified, the default location for Linux and OSX are used (/usr/local/cuda/lib and /Developer/GPU\ Computing/C/common/inc, respectively).

Step 5
- The TSNE, TSNE_D, and TSNE_P functions are now ready to use. If compilation of the CUDA software failed, the functions will fall back on a Matlab implementation of t-SNE.


Potential pitfalls
==================

- Please make sure that your CUDA version is built for the same architecture as your MATLAB version. For instance, it is not possible to combine a 64-bit CUDA version with a 32-bit MATLAB version. Using a 32-bit CUDA version with 64-bit MATLAB is possible, but requires some changes to the 'mexall' function (i.e., the -m32 switch needs to be added).

- If the CUDA code does not start at runtime, please check whether the dynamic linker can find the required CUDA libraries (cudart, cublas, cufft). It might be necessary to set the LD_LIBRARY_PATH or DYLD_LIBRARY_PATH environment variables. Please run Matlab without GUI to make sure you see all error messages.

- If the CUDA code starts, but suddenly quits with an unclear error message, you might have run out of GPU memory. Please try to reduce the number of data points in the data, or find a GPU with more RAM. 


Contact
=======

For questions, suggestions, or bugfixes, please contact:

			lvdmaaten@gmail.com

(But do not email with questions that are answered in this document!)
