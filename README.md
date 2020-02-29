# jet-spack

  Configure JET with the software packages for JEDI 


# **For general users**

  ## Configurate spack

  - for bash users, edit `~/.bashrc` etc.
  
    ```
    export SPACK_ROOT=/misc/whome/Xin.L.Zhang/spack
    . ${SPACK_ROOT}/share/spack/setup-env.sh
    ```

  - for csh/tcsh users, edit , edit `~/.cshrc` etc.
    ```
    setenv SPACK_ROOT /misc/whome/Xin.L.Zhang/spack
    source ${SPACK_ROOT}/share/spack/setup-env.csh
    ```

  ## Load packages

  - [x] For Intel compiler version 18.0.5
  
    append following lines to `~/.bashrc` or `~/.cshrc` or ....:
   
    ```
    module purge
    module load intel/18.0.5.274
    module load impi/2018.4.274
    module load cmake/3.6.1
    
    # spack load has some problem, so use module load
    module load netcdf-c-4.7.3-intel-18.0.5-wbmurwb
    module load netcdf-fortran-4.5.2-intel-18.0.5-zxprvut
    module load hdf5-1.10.6-intel-18.0.5-gynln47
    module load eigen-3.3.7-intel-18.0.5-k4bnahc
    module load fftw-3.3.8-intel-18.0.5-r6gmk32
    # spack has problem to build boost, just use the gnu version
    module load boost-1.72.0-gcc-9.2.0-i2w2xrm
    # Set the path of MKL
    setenv MKL_PATH /apps/intel/parallel_studio_xe_2018.4.057/compilers_and_libraries_2018/linux/mkl
    ```
  - set `NETCDF/PNETCDF` ( for WRF users)
  
    ```
    setenv NETCDF `spack location -i netcdf-fortran@4.5.2%intel@18.0.5`
    setenv NETCDF_C `spack location -i netcdf-c@4.7.3%intel@18.0.5`
    module load parallel-netcdf-1.12.1-intel-18.0.5-zx5tjzg
    setenv PNETCDF `spack location -i parallel-netcdf@1.12.1%%intel@18.0.5`
    ```
    
  - [x] For GNU compiler version 9.2.0
  
    append following lines to `~/.bashrc` or `~/.cshrc` or ....:
   
    ```
    module load gnu/9.2.0
    module load openmpi/3.1.4
    module load cmake/3.6.1
    
    spack load -r netcdf-fortran@4.5.2%gcc@9.2.0
    spack load -r eigen@3.3.7%gcc@9.2.0
    spack load -r boost@1.72.0%gcc@9.2.0
    spack load -r netlib-lapack@3.8.0%gcc@9.2.0
    spack load -r fftw@3.3.8%gcc@9.2.0
    setenv LAPACK `spack location -i netlib-lapack@3.8.0%gcc@9.2.0` for csh/tcsh
    or
    export LAPACK=`spack location -i netlib-lapack@3.8.0%gcc@9.2.0` for bash
    ```
  - set `NETCDF/PNETCDF` ( for WRF Users)
  
    ```
    setenv NETCDF `spack location -i netcdf-fortran@4.5.2%gcc@9.2.0`
    setenv NETCDF_C `spack location -i netcdf-c@4.7.3%gcc@9.2.0`
    spack load -r parallel-netcdf@1.12.1%gcc@9.2.0
    setenv PNETCDF `spack location -i parallel-netcdf@1.12.1%gcc@9.2.0`
    ```

---
---

# **For developers**

  ## Prepare mirror on a platform with *FULL* internet access

  - spack mirror add jedi file:///misc/whome/Xin.L.Zhang/mirror

  ## Installation

  - Intel compiler

    - [x] module load intel/18.0.5.274
    - [x] spack compiler find
    - [x] module load impi/2018.4.274
    - [x] module load cmake/3.6.1
  
    - [x] spack install eigen+fftw %intel@18.0.5 arch=haswell
    - [x] spack install boost arch=haswell
    - [x] spack install netcdf-fortran %intel@18.0.5 arch=haswell
  
    - [x] spack install parallel-netcdf %intel@18.0.5 arch=haswell


  - GNU compiler
  
    - [x] module load gnu/9.2.0
    - [x] spack compiler find
    - [x] module load openmpi/3.1.4
    - [x] module load cmake/3.6.1
    
    - [x] spack install eigen+fftw %gcc@9.2.0 arch=haswell
    - [x] spack install boost %gcc@9.2.0 arch=haswell
    - [x] spack install netcdf-fortran %gcc@9.2.0 arch=haswell
    - [x] spack install netlib-lapack %gcc@9.2.0 arch=haswell
  
    - [x] spack install parallel-netcdf %gcc@9.2.0 arch=haswell
