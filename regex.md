# Resumo do livro do Piazinho.
## Capítulo 2

### Representantes

| Metacaractere | Função| 
|:-----:|-----|
| .   | Um caractere qualquer| 
| []  | Lista de caracteres permitidos e são literais|  
|  [^]| Lista de caracteres proibidos |

### Quantificadores

| Metacaractere |	Função |
|:----:|----|	
|?    | Zero ou um caractere(Opcional)|
|*	|Zero ou mais(Curinga)|
|+|	Um ou mais (Não opcional, pelo menos um)|
|{n,m}	|De n até m(Controle)|

### Âncoras

|Metacaractere	| Função|
|:----:|-----|
|^|	Início da linha(fica fora da lista)|
|$|	Fim da linha |
|\b|	Borda, início ou fim da palavra|

* ^[^0-9]		Início da linha	
* ^$ 		linha vazia
* ^.{20,60}	linhas que tenham entre 20 e 60 caracteres
* \bdia		dia, diagragma, bom-dia
* dia\b		dia, melodia, bom-dia

### Outros

|Metacaractere|	Função|
|:---:|---|
|\c|	Escape, torna o caractere c literal|
|	\| |Um ou outro(alternativa)|
|()|	Delimita um grupo|
|\1...\9|	Retrovisor, usado para casar grupos de 1-9 (casa trechos já casados, útil quando se sabe o que será casao máximo são 9)|



