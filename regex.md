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

* Boa-tarde|boa-noite
* (ha!)+				ha!, ha!ha! ....
* (\.[0-9]){3}			.0.1.2, .2.3.6 ...
* Boa-(tarde|noite)		Boa-tarde, Boa-noite
* (# | n\.|núm) 7			# 7, n. 7, núm 7
* (in|con)?certo			incerto, concerto, certo
* ((su|hi)per)?mercado		mercado, supermercado, hipermecardo
* [[:alpah:]_]+\(\)			útil para achar funções em códigos
* (quero)-\1			quero-quero
* ([A-Za-z]+)-\1			quero-quero, bate-bate
* ([A-Za-z]+)-?\1			quero-quero, bate-bate, bombom, lili, dudu, bibi 
* \b([A-Za-z]+)-?\1\b
* (lenta)(mente) é \2 \1		lentamente é mente lenta
* ((band)eira)nte \1 \2		bandeirante badeira banda
* ((((a)b)c)d)-1 \1,\2,\3,\4	abcd-1 = abcd, abc, ab,a
* Contar os parênteses da esquerda para a direita, esse vai ser o número do retrovisor.
* O retrovisor referencia o texto casado, encontrado, e não a expressão regular do grupo.
* ([0-9])\1	66 mas não casa com 69 porque o \1 é 6, dessa forma, só casa números iguais.


