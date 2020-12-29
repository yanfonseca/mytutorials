## Python

## Pip

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

## Ipython

* pip install ipython[notebook]

* python3 manage.py shell

* pip install django-extensions

* python3 manage.py shell_plus --notebook
abre o notebook com funções do django


## Dicas:

* Bibliotecas que podem ter o que você procura:
      
1. functools
2. collections

## OO
```
class Conta:
    __codigo = 100

    def __init__(self, nome, saldo):
        self.__nome = nome
        self.__saldo = saldo
        self.__limite = 500

    def __str__(self):
        resumo = f"""
        nome: {self.__nome} 
        saldo: {self.__saldo} 
        limite: {self.__limite}
        """
        return resumo

    @property
    def saldo(self):
        return self.__saldo

    @property
    def limite(self):
        return self.__limite

    @limite.setter
    def limite(self, limite):
        self.__limite = limite

    @staticmethod
    def dono():
        return "Brasil"

class BB(Conta):
    
    def __init__(self, nome, saldo, estado):
        Conta.__init__(self, nome, saldo)
        self.__estado = estado

    def __str__(self):
        resumo = f"""
        nome: {self._Conta__nome} 
        saldo: {self._Conta__saldo} 
        limite: {self._Conta__limite}
        estado: {self.__estado}
        """
        return resumo
        

class Itau(Conta):
    def __init__(self, nome, saldo, categoria):
        Conta.__init__(self, nome, saldo)
        self.__categoria = categoria

    def __str__(self):
        resumo = f"""
        nome: {self._Conta__nome} 
        saldo: {self._Conta__saldo} 
        limite: {self._Conta__limite}
        categoria: {self.__categoria}
        """
        return resumo

class ContasAbertas():
    def __init__(self, contas):
        self.__contas = contas

    def __getitem__(self, item):
        return self.__contas[item]

    def __len__(self, item):
        return len(self.__contas)

```

## Abstract class

```
from collections.abc import MutableSequence

class MinhaListinhaMutavel(MutableSequence):
    pass

objetoValidado = MinhaListinhaMutavel()
print(objetoValidado)
```

## Decorator
```
def eleva_ao_quadrado(func):
    def func_decorada(*arg):
        mult = func(*arg)
        return mult ** 2
    return func_decorada

from functools import reduce

@eleva_ao_quadrado
def multiplica(*args):
    return reduce((lambda numero_a, numero_b: numero_a * numero_b), args)

print(multiplica(2,3,2))
```
