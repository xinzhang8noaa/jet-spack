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
## For WRF users:

  - set `NETCDF/PNETCDF`
  
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

## Installation


  - [x] spack install eigen+fftw arch=haswell
  - [x] spack install boost arch=haswell
  - [x] spack install netcdf-fortran arch=haswell
  - [x] spack install netlib-lapack arch=haswell
  
  - [x] spack install parallel-netcdf arch=haswell
