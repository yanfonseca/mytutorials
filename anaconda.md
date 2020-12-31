# How to use Anaconda

### Basic

    conda --help

    conda list: It lists all packages currently installed.

    conda install foo-lib=12.3 : Semantic versioning

    conda install foo-lib=14.3.2

    conda install 'bar-lib=1.0|1.4*' : Install 1.0 version or 1.4 something.

    conda install 'bar-lib>1.3.4,<1.1'

    conda update pkg

    conda remove pkg1 pkg2

    conda search pkg

    conda search cytoolz=0.8.2 --info : It will report on all avaible package versions.

    conda search --channel davidmertz --override-channels --platform linux-64

    anaconda search textadapter

    conda install --channel my-organization the-package

### Environment

    conda env list

    conda activate ENV

    conda deactivate

    conda create --name recent-pd python=3.6 pandas=0.22 scipy statsmodels

    conda env remove --name ENVNAME

    conda export -n ENV

    conda env create --file file-name.yml

### Anaconda Project

* Useful to share projects.

      anaconda-project




