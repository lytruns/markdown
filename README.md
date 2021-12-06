# <h1 align="center">MotorHead</h1>

<h4 align="center"> 
🚧  MotorHead Lib´s  🚀 Em desenvolvimento...  🚧
</h4>


<h3 align="center">
    <a href="https://www.fontes.intranet.bb.br/bi/bigmotorhead">🔗CLI MOTORHEAD</a>
</h3>


## Introdução

<p align="justify"> :robot: MotorHead - (MH) é uma ferramenta desenvolvida buscando fornecer aos desenvolvedores de modelos a possibilidade de verificar a interpretação de seus códigos bem como recomendar um padrão de codificação. Ele também pode procurar por certos tipos de erros, recomendando sobre como blocos específicos podem ser refatorados oferecendo detalhes sobre a complexidade do código.

<p align="justify"> :robot: MH se baseia em bibliotecas semelhantes como pychecker (agora extinto), pyflakes, flake8 e mypy, trazendo em seu “Core” o padrão próximo ao PEP 8. A biblioteca exibirá uma série de mensagens enquanto analisa o código e também pode ser usado para exibir algumas estatísticas sobre o número de avisos e erros encontrados em arquivos diferentes. As mensagens são classificadas em várias categorias, como erros e avisos.:robot: </p>

<p align="justify"> :robot:Por último, mas não menos importante, o código recebe uma classificação geral, com base no número e na gravidade dos avisos e erros.
É importante descrever que o MotorHead não tem como objetivo dificultar o processo de desenvolvimento de modelos e scripts mas sim criar uma padronização que facilitará seu modelo subir para produção com todas as características básicas de um código limpo e eficiente. A biblioteca esforça para relatar o mínimo possível de falsos positivos para erros, mas pode ser muito prolixo com avisos. Isso ocorre, por exemplo, porque ele tenta detectar coisas que podem ser perigosas em um contexto, mas não o são em outros, ou porque verifica algumas coisas com as quais você não se importa. Geralmente, você não deve esperar que o MotorHead seja totalmente silencioso sobre o seu código, então não necessariamente se assuste se ele enviar um monte de mensagens para o seu projeto!.:robot: </p>



## Instalação

<p align="justify"> :robot:Pylint deve ser facilmente instalável usando pip..:robot: </p>

~~~python
!pip install big_motorhead==1.0.2 --user
~~~

## Executando MotorHead

### Invocando MotorHead

<p align="justify"> :robot:O Pylint deve ser chamado a partir da linha de comando. O uso é.:robot: </p>

~~~python
big_motorhead [options] arquivos | diretórios
~~~


<p align="justify"> :robot:Você deve dar ao MotorHead o nome de um arquivo ou pasta onde contém os arquivos indicando a localização pelo caminho relativo ou completo, sujeito às mesmas regras e configuração utilizadas em outros pacotes python. Deve-se prestar atenção ao na indicação do arquivo, pois é um erro comum analisar o trajeto até o arquivo selecionado não passando sua extensão final.:robot: </p>

<p align="justify"> :robot:
Também é possível analisar arquivos ". IPYNB", tendo em mente que o MotorHead tentará converter o nome do arquivo em um nome de módulo “.py” e só será capaz de processar o arquivo se for bem-sucedido.:robot: </p>



### Verificando arquivos

<p align="justify"> Uma modelo obrigatoriamente deverá possuir os arquivos README.md | requirements.txt | .gitignore , apenas com o conjunto desses arquivos será possível dar proseguimento do modelo para a esteira de produção. Para a verificação em sua pasta de todos os atributos necessários é invocado o comando: </p>

~~~python
!python3 -m big_motorhead.cli -d
~~~

<p align="justify"> No caso da ausência de alguns dos arquivos será exibido uma mensagem de advertência da seguinte forma: </p>

```diff
Não foi encontrado os seguintes arquivos para validar a estrutura
```

```diff
README.md | requirements.txt | .gitignore 
```

<p align="justify"> No caso em que todos os requisitos sejam atendidos será exibido: </p>
    


<p align="justify">Desta forma é necessário executar essa verificação através dos comandos: : </p>

~~~python
!python3 -m big_motorhead.cli -d
~~~

<p align="justify">No caso da ausência de alguns dos arquivos citados acima será exibido uma resposta:</p> 

```diff
- Não foi encontrado os seguintes arquivos para validar a estrutura: 
```

```diff
! README.md | requirements.txt | .gitignore 
```

<p align="justify"> Na presença de todos os arquivos necessários para atender a estrutura do modelo:</p> 


```diff
+ PASSED                     100%
```



Verificar os erros de sintaxe do .ipynb



~~~python
!python3 -m big_motorhead.cli -f arquivos.ipynb
~~~




# Mais informações PEP8
<details>
  <summary>Layout de código</summary>
## Recuo  
<p align="justify">As linhas de continuação devem alinhar os elementos agrupados verticalmente, usando a linha implícita do Python, juntando-se entre parênteses, colchetes e colchetes, ou usando um recuo suspenso. Ao usar um recuo deslocado, o seguinte deve ser considerado; não deve haver argumentos na primeira linha e recuo adicional deve ser usado para se distinguir claramente como uma linha de continuação:</p> 


```python
# Correto:

# Alinhado com o delimitador de abertura.
foo = long_function_name(var_one, var_two,
                         var_three, var_four)

# Adicione 4 espaços (um nível extra de recuo) para distinguir os argumentos do resto.
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)

# Os recuos pendurados devem adicionar um nível.
foo = long_function_name(
    var_one, var_two,
    var_three, var_four)
```

    
    

```python
# Errado:

# Argumentos na primeira linha proibidos quando não estiver usando alinhamento vertical.
foo = long_function_name (var_one, var_two,
    var_three, var_four)

# Indentação adicional necessária, pois a indentação não é distinguível.
def long_function_name (
    var_one, var_two, var_three,
    var_four):
    imprimir (var_one)
```
    
</p>
</details> 













  
