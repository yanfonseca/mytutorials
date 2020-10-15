# Python

## Pip
* Verificar se está instalado

python3 -m pip --version

* Se não estiver

sudo apt update
sudo apt install python3-pip
pip3 --version

## Environment

python3 -m pip install --user -U virtualenv
python3 -m virtualenv filepath

* Para ativar a env 
source filepath/bin/activate

* Para desativar a env
deactivate
  
### Env para Machine Learning

python3 -m pip install -U jupyter matplotlib numpy pandas scipy scikit-learn

* Se foi criada a env, como sugerido acima, é necessário registrar ao jupyter e dar um nome
python3 -m ipykernel install --user --name=python3
