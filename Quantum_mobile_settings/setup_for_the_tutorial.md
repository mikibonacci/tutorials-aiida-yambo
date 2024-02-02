# QM modifications to support yambo-5.2.1 and tutorials.

- set at least 2 cores

- open the terminal

## (1) code compilation

we need yambo 5.2.1 for the aiida-yambo part; if you want to run also the
aiida-yambo-wannier90 part, you need also to compile qe in its develop branch.

### `yambo-5.2.1`. load the yambo environment: it has already a lot of things.
```bash
conda activate yambo
```

### download version of yambo:
```bash
cd ~/.conda/envs/yambo
git clone https://github.com/yambo-code/yambo.git 
cd yambo-5.2.1
git checkout 5.2.1
```

### install missing packages for compilation:
```bash
conda install gfortran=13.2.0
conda install scalapack
```

### configure and make:
```bash
export PATH_YAMBO_LIB="/home/max/.conda/envs/yambo"
./configure --enable-mpi --enable-open-mp --with-fft-path=$PATH_YAMBO_LIB --with-hdf5-path=$PATH_YAMBO_LIB --with-netcdf-path=$PATH_YAMBO_LIB --with-netcdff-path=$PATH_YAMBO_LIB --disable-hdf5-par-io --with-libxc-path=$PATH_YAMBO_LIB --with-scalapack-libs=$PATH_YAMBO_LIB/lib/libscalapack.so --with-blacs-libs=$PATH_YAMBO_LIB/lib/libscalapack.so --enable-par-linalg

make yambo
make core
```

### `qe_develop`. load the qespresso environment: it has already a lot of things.
```bash
conda activate qespresso
```

### download version of qe-develop:
```bash
cd ~/.conda/envs/qespresso
git clone https://gitlab.com/QEF/q-e.git qe-develop
cd qe-develop
git checkout develop
```

### install missing packages for compilation, and compile:
```bash
conda install gfortran=13.2.0
./configure
make all
```

## `aiida` environment. Prepare the codes and the tutorial-files:

```bash
workon aiida
```
### Install the aiida-yambo and the aiida-yambo-wannier90 plugins:
```bash
cd /home/max/.conda/envs/yambo
mkdir plugins
cd plugins
git clone https://github.com/yambo-code/aiida-yambo.git
pip install -e aiida-yambo/
git clone https://github.com/aiidaplugins/aiida-yambo-wannier90.git
pip install -e aiida-yambo-wannier90/
verdi daemon stop; verdi -p generic storage migrate
```

### Download the files:
```bash
cd /home/max
git clone https://github.com/mikibonacci/tutorials-aiida-yambo.git
```

### last step: install the codes in the aiida db

```bash
cd tutorials-aiida-yambo/Quantum_mobile_settings
verdi code setup --config yambo_code.yml
verdi code setup --config p2y_code.yml
verdi code setup --config ypp_code.yml
verdi code setup --config pw_dev_code.yml
verdi code setup --config pw2wannier90_dev_code.yml
verdi code setup --config projwfc_dev_code.yml
verdi code setup --config gw2wannier90_code.yml
verdi code setup --config wannier90_code.yml
```


