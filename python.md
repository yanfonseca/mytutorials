## Python

### Pip

#### Comandos básicos
      pip --help

      pip list
      
      pip --version

* Verificar se está instalado

      python3 -m pip --version

* Se não estiver

      sudo apt update
      sudo apt install python3-pip
      pip3 --version

### Instalar com o pip

- requirements.txt is a list of packages.

      pip install -r requirements.txt 

      pip install package1 package2.

### Environment

* Instalar a virtualenv

      python3 -m pip install --user -U virtualenv

* Instalar a virtualenv dentro de uma pasta

      python3 -m virtualenv nome_da_env

* Como alternativa pode usar a venv

      sudo apt-get install python3-venv

* Para ativar a env 

      source nome_da_env/bin/activate

* Para desativar a env

      deactivate
  
### Env para Machine Learning

      python3 -m pip install -U jupyter matplotlib numpy pandas scipy scikit-learn

* Se foi criada a env, como sugerido acima, é necessário fazer o registro:

      python3 -m ipykernel install --user --name=python3

* Para ativar o 
      
      jupyter notebook 
