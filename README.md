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
    spack load -r gcc@9.2.0
    spack load -r netcdf-fortran%gcc@9.2.0
    spack load -r cmake%gcc@9.2.0
    spack load -r eigen%gcc@9.2.0
    spack load -r boost%gcc@9.2.0
    spack load -r netlib-lapack%gcc@9.2.0
    setenv LAPACK `spack location -i netlib-lapack` for csh/tcsh
    or
    export LAPACK=`spack location -i netlib-lapack` for bash
    ```
## For WRF users:

    setenv NETCDF `spack location -i netcdf-fortran`
    setenv NETCDF_C `spack location -i netcdf-c`
    spack load -r parallel-netcdf@1.12.1
    setenv PNETCDF `spack location -i parallel-netcdf@1.12.1`

---
---

# **For developers**

## Prepare mirror on a platform with *FULL* internet access

## Installation

  - [x] spack install gcc@9.2.0
  - [x] spack load -r gcc@9.2.0
  - [x] spack install netcdf-fortran%gcc@9.2.0
  - [x] spack install boost%gcc@9.2.0
  - [x] spack install eigen%gcc@9.2.0
  - [x] spack install netlib-lapack%gcc@9.2.0
