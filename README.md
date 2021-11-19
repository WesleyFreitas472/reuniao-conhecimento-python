# Python 3

[__TOC__]

## Conceitos Básicos

### Variáveis

Exemplos de alguns tipos simples de variáveis:

* int: 1, 10, 15, 30000000000000;
* float: 3.42, 1.2;
* str: 'Python', "DevOps";
* bool: True/False;

O tipo de uma variável é definido pelo valor que ela recebe.

### Operações Matemáticas

#### Operadores Aritméticos

* \+   
  * `x + 10`
* \-   
  * `x - 10`
* \*   
  * `x * 10`
* /    
  * `x / 10`
* \*\* 
  * `x ** 2`
* %    
  * `x % 10`

## Entrada e saída

### Entrada

```python
nome = input('Digite seu nome: ')
```

### Saída

```python
print('Olá, ' + nome)
```

## Blocos Condicionais

Para controle de fluxo python possui os blocos if, elif e else.

```python
if  x > 10:
    print('x é maior que 10')
elif x < 10:
    print('x é menor que 10')
else:
    print('x é igual a 10')
```

Python também possui um if ternário (apenas uma linha).

```python
x = 10 if x > 10 else 0
```


### Operadores Relacionais

|Operador |	Descrição | Exemplo
| ------- | ---------- | --------
|== | Igual	| (A == B) | false
|!= | Não igual	| (A != B) | true
|> | Maior que	| (A > B) | false
|< | Menor que	| (A < B) | true
|>= | Maior ou igual que | (A >= B) | false
|<= | Menor ou igual que | (A <= B) | true

### Operadores Lógicos

|Operador | Exemplo | Saída
| ------- | -------- | --------
| and | (A and B) | True se A E B são True, False caso contrário
| or |  (A or B) | True se A OU B são True, False caso contrário
| not | (not B) | True se B é False, False caso contrário

## Bloco de Repetição

Para laços de repetição Python possui duas instruções: while e for.

### while

Executa um bloco de código enquanto uma codição for verdadeira.

```python
x = 10
while x < 10:
    print(x)
    x = x - 1
```

### for

Executa um bloco de código para item de uma conjunto de dados.

```python
s = 'Python'
for letra in s:
    print(letra)
```

## Estrutura de Dados

Python possui 3 estruturas de dados padrão: lista, tupla, set e dicionário.

### Lista

Listas são uma sequencia de objetos, portanto podem conter itens de qualquer tipo.

```python
lista = [1, 2, 3, 4, 5]
print(lista)
lista2 = [1, "a", True, 3.14]
```

Para adicionar um item em uma lista usar o método append.

```python
lista.append(6)
```

Para remover um item de uma lista podemos usar o método remove ou pop. O método remove remove o item especificado, o método pop remove o último item da lista ou o item de dada posição retornando o item removido.

**remove**:

![img](img/list-remove.png)

**pop**:

![img](img/list-pop.png)


#### List Comprehension

Para criar uma lista podemos utilizar também o list comprehension.

![img](img/list-comprehension.png)

## Tupla

Tuplas são semelhantes a listas mas são imutáveis. Isso quer dizer que uma tupla, depois de criada, não pode ser alterada.

```python
tupla = (1, 2, 3, 4, 5)
print(tupla)
tupla2 = (1, "a", True, 3.14)
```

> Não existe tuple comprehension!

## Set

Sets também são muito semelhantes a listas, mas não permitem itens repetidos.

```python
s = {3.14, 3.14, 1, "python"}
```

No exemplo acima o set será criado sem erro mas apenas um dos itens `3.14` será adicionado.

![img](img/set-comprehension.png)


Para adicionar um item no set podemos utilizar o método add.

![img](img/set-add.png)

Para remover um item podemos utiliar o método remove ou discard.

![set-remove](img/set-remove.png)

> Note que o método remove dispara uma exception caso o item não exista no set e o método discard não dispara nenhuma exception.

## Dicionário

O dicionário é a implementação de uma estrutura chave valor. A chave precisa ser de tipos primitivos e o valor pode ser de qualquer tipo.

![dict](img/dict.png)

Para adicionar um valor do dicionário basta referenciar a chave dentro de colchetes.

```python
print(d["chave1"])
```

> Se a chave não existir no dicionário será retornado um erro.

Também é possível através do método get.

```python
value = d.get("chave1")
print(value)
```

> O método get retorna None caso a chave não exista.

Para adicionar itens no dicionário basta fazer como no exemplo abaixo.

```python
d["chave2"] = "valor2"
print(d["chave2"])
```

Se a chave for repetida o valor será substituido.

Por fim, para remover um item do dicionário podemos utilizar a palavra-chave del.

```python
d["chave2"] = "valor2"
del d["chave2"]
print(d["chave2"])
```

> Note que o exemplo acima irá disparar uma exception no comando print pois a chave foi deletada na instrução anterior.

## Arquivos

Podemos abrir um arquivo em python usamos a função `open`. Essa função espera dois parametros, o primeiro é o caminho do arquivo e o segundo é o modo de abertura.

```python
file = open("arquivo.txt", "r") #abre um arquivo no modo de leitura
file = open("new_file.txt", "w") #cria um novo arqruivo e abre no modo escrita
file = open("existing_file.txt", "a") #abre o arquivo no modo append, um modo escrita para arquivos que já existem
```

É importante fechar o arquivo após utilizar, para isso utilize a função close.

```python
file = open("arquivo.txt", "r") #abre um arquivo no modo de leitura
print(file.read()) #imprime o conteúdo do arquivo
file.close()
```

Também podemos utilizar a palavra-chave `with` para abrir e fechar o arquivo automaticamente.

```python
with open("arquivo.txt", "r") as file:
    print(file.read())
```

## Exceptions

A exception representa uma anomalia ou uma situação que precisa ser tratada especificamente. Quando uma exception é lançada o programa é interrompido e a mensagem de erro é exibida. Podemos evitar que isso aconteça usando o try/except.

![exception](img/exception.png)

## Funções

Funções são um bloco de código associado a um nome e que pode ser executado a qualquer momento. A função pode receber parâmetros e retornar um valor.

```python
def soma(a, b):
    return a + b

resultado = soma(1, 2)
print(resultado)
```

É possível criar uma função que recebe um número infinito de parametros posicionais.

```python
def somatorio(*nums):
    resultado = 0
    for num in nums:
        resultado += num
    return resultado

soma = somatorio(1,2,3,4,5)
print(soma)
```

Também é possível criar uma função que recebe um número infinito de parametros nomeados.

```python
def welcome(nome, **kwargs):
    print("Olá " + nome)

    local = kwargs.get('local')
    if local:
        print("Seja bem vindo de volta a " + local)

welcome("Wesley", local="Softplan")
```

## Módulo

Um módulo em python é um arquivo que contém funções e variáveis. Esse arquivo tem a extensão `.py` e pode ser importado em outro arquivo.

Imagine que existe o seguinte arquivo chamado calc.py

```python
def soma(a, b):
    return a + b

def sub(a, b):
    return a - b
```

Em um outro arquivo ou em um terminal podemos fazer o seguinte:

```python
import calc

print(calc.soma(1, 2))

print(calc.sub(1, 2))
```

No exemplo acima estamos importando o módulo calc e executando as funções soma e sub.

Se quiséssemos importar apenas uma função do módulo podemos utilizar o comando `from`.

```python
from calc import soma

print(soma(1,2))
```

Se o intuito é importar tudo do arquivo soma poderíamos utilizar o operador `*`.

```python
from calc import *

print(soma(1,2))
```

## Classes

Python é uma linguagem de programação multiparadigma. Um dos paradigmas suportados é a orientação a objetos.

Estrutura básica de uma classe é:

```python
class Caneta:
    def __init__(self, cor):
        self.cor = cor

    def escrever(self):
        print("Estou escrevendo com a cor " + self.cor)

caneta = Caneta("azul")
caneta.escrever()
```

No exemplo acima criamos a classe Caneta. O método \__init\__ é executado automaticamente quando a classe é instanciada. O primeiro parâmetro de qualquer método da classe é sempre uma referencia para o objeto que está sendo manipulado.

## Herança

Classes podem receber herança de outras classes. Uma coisa interessante do python é que há a possibilidade de se utilizar herança múltipla.

```python
class MaterialEscolar:
    def __init__(self, proprietario):
        self.proprietario = proprietario
    def dono(self):
        print("O proprietário é " + self.proprietario)

class Caneta(MaterialEscolar):
    def __init__(self, proprietario, cor):
        super().__init__(proprietario)
        self.cor = cor
    def escrever(self):
        print("Estou escrevendo com a cor " + self.cor)

caneta = Caneta("Wesley", "azul")
caneta.escrever() #imprime "Estou escrevendo com a cor azul"
caneta.dono() #imprime "O proprietário é Wesley"
```
