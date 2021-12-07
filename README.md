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




### Mais informações PEP8
<details>
  <summary>Layout de código</summary>
    
### Recuo  
    
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

    
<p align="justify">Quando a parte condicional de uma instrução if é longa o suficiente para exigir que seja escrita em várias linhas, é importante notar que a combinação de uma palavra-chave de dois caracteres (ou seja, if ), mais um único espaço, mais um parêntese de abertura cria um natural Recuo de 4 espaços para as linhas subsequentes da condicional multilinha. Isso pode produzir um conflito visual com o conjunto recuado de código aninhado dentro da instrução if , que também seria recuado naturalmente para 4 espaços. Este PEP não assume uma posição explícita sobre como (ou se) distinguir visualmente essas linhas condicionais do conjunto aninhado dentro da instrução if . As opções aceitáveis nesta situação incluem, mas não estão limitadas a:</p>     
    

```python
# Na identação extra.
if (this_is_one_thing and
    that_is_another_thing):
    do_something()

# Adicione um comentário, que fornecerá alguma distinção aos editores
# apoiando o realce de sintaxe.
if (this_is_one_thing and
    that_is_another_thing):
    # Since both conditions are true, we can frobnicate.
    do_something()

# Adicione algum recuo extra na linha de continuação condicional.
if (this_is_one_thing
        and that_is_another_thing):
    do_something()
```
 
    
<p align="justify">A chave / colchete / parêntese de fechamento em construções de várias linhas podem se alinhar sob o primeiro caractere diferente de espaço em branco da última linha da lista, como em:</p>   
    
```python
my_list = [
    1, 2, 3,
    4, 5, 6,
    ]
    
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
    )
```

<p align="justify"> ou pode ser alinhado sob o primeiro caractere da linha que inicia a construção multilinha, como em:</p> 
  
```python
my_list = [
    1, 2, 3,
    4, 5, 6,
]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
)
```

    
### Tabs ou Spaces
    
<p align="justify"> Os espaços são o método de indentação preferenciais. As guias devem ser usadas exclusivamente para manter consistentes o código que já está indentado com tabs. Python não permite a mistura de tabulações e espaços para indentação.</p> 
    
#### Comprimento Máximo da Linha
    
<p align="justify"> Para blocos longos de texto fluidos com menos restrições estruturais (docstrings ou comentários), o comprimento da linha deve ser limitado a 72 caracteres.

Essa limitação é indicada visando que seja possivel vários arquivos abertos lado a lado no editor e funciona bem ao usar ferramentas de revisão de código que apresentam as duas versões em colunas adjacentes.

O empacotamento padrão na maioria das ferramentas interrompe a estrutura visual do código, tornando-o mais difícil de entender. Os limites são escolhidos para evitar quebra nos editores com a largura da janela definida como 80, mesmo se a ferramenta colocar um glifo de marcador na coluna final ao quebrar as linhas. Algumas ferramentas baseadas na web podem não oferecer quebra de linha dinâmica.

Algumas equipes preferem um comprimento de linha mais longo. Para código mantido exclusiva ou principalmente por uma equipe que pode chegar a um acordo sobre esse problema, não há problema em aumentar o limite de comprimento da linha para 99 caracteres, desde que os comentários e docstrings ainda tenham 72 caracteres.

A biblioteca padrão do Python é conservadora e requer linhas limitadas a 79 caracteres (e docstrings / comentários a 72).

A maneira preferida de quebrar linhas longas é usando a continuação de linha implícita do Python entre parênteses, colchetes e colchetes. Linhas longas podem ser quebradas em várias linhas envolvendo as expressões entre parênteses. Eles devem ser usados em vez de usar uma barra invertida para a continuação da linha.

Barras invertidas ainda podem ser apropriadas às vezes. Por exemplo, long, multiple with -statements não podem usar continuação implícita, então barras invertidas são aceitáveis:.</p> 


```python
with open('/path/to/some/file/you/want/to/read') as file_1, \
     open('/path/to/some/file/being/written', 'w') as file_2:
    file_2.write(file_1.read()) 
```
    
<p align="justify"> Durante décadas, o estilo recomendado era interromper depois de operadores binários. Mas isso pode prejudicar a legibilidade de duas maneiras: os operadores tendem a se espalhar por colunas diferentes na tela, e cada operador é movido para longe de seu operando e para a linha anterior. Aqui, o olho tem que fazer um trabalho extra para dizer quais itens são adicionados e quais são subtraídos: </p>  
    
    
 ```python
# Errado: 
# operadores ficam longe de seus operandos 
income = (gross_wages +
          taxable_interest +
          (dividends - qualified_dividends) -
          ira_deduction -
          student_loan_interest)
```

<p align="justify"> Para resolver esse problema de legibilidade, os matemáticos e seus editores seguem a convenção oposta. Donald Knuth explica a regra tradicional em sua série Computers and Typesetting : "Embora as fórmulas dentro de um parágrafo sempre quebrem após as operações e relações binárias, as fórmulas exibidas sempre quebram antes das operações binárias". Seguir a tradição da matemática geralmente resulta em um código mais legível: </p>  

 ```python
# Correto: 
# fácil de combinar operadores com 
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```

<p align="justify"> No código Python, é permitido interromper antes ou depois de um operador binário, desde que a convenção seja consistente localmente. Para o novo código, o estilo de Knuth é sugerido.</p>

    
### Linhas em Branco
    
<p align="justify"> Envolva as funções de nível superior e as definições de classe com duas linhas em branco.

As definições de método dentro de uma classe são circundadas por uma única linha em branco.</p>

<p align="justify"> Linhas em branco extras podem ser usadas (com moderação) para separar grupos de funções relacionadas. Linhas em branco podem ser omitidas entre um monte de linhas simples relacionadas (por exemplo, um conjunto de implementações fictícias).</p>

<p align="justify"> Use linhas em branco nas funções, com moderação, para indicar seções lógicas.</p>

<p align="justify"> Python aceita o caractere de feed de formulário control-L (ou seja, ^ L) como espaço em branco; Muitas ferramentas tratam esses caracteres como separadores de página, portanto, você pode usá-los para separar páginas de seções relacionadas de seu arquivo. Observe que alguns editores e visualizadores de código baseados na web podem não reconhecer control-L como um feed de formulário e exibirão outro glifo em seu lugar. </p>
    

 ### Codificação do arquivo fonte
    
 <p align="justify"> O código na distribuição central do Python deve sempre usar UTF-8 e não deve ter uma declaração de codificação.</p>

 <p align="justify"> Na biblioteca padrão, codificações não UTF-8 devem ser usadas apenas para fins de teste. Use caracteres não ASCII com moderação, de preferência apenas para denotar lugares e nomes humanos. Se estiver usando caracteres não ASCII como dados, evite caracteres Unicode barulhentos como z̯̯͡a̧͎̺l̡͓̫g̹̲o̡̼̘ e marcas de ordem de bytes.</p>

 <p align="justify"> Todos os identificadores na biblioteca padrão do Python DEVEM usar identificadores somente ASCII e DEVEM usar palavras em inglês sempre que possível (em muitos casos, abreviações e termos técnicos são usados ​​que não são em inglês).</p>

 <p align="justify"> Os projetos de código aberto com um público global são incentivados a adotar uma política semelhante.</p>
    
  ### Importações
    
  <p align="justify"> As importações geralmente devem ser feitas em linhas separadas:</p>
    
```python
# Correto:
import os
import sys
```

   ```python
# Errado:
import sys, os
```
    
<p align="justify"> As importações são sempre colocadas no início do arquivo, logo após quaisquer comentários do módulo e docstrings, e antes das constantes e globais do módulo.

As importações devem ser agrupadas na seguinte ordem:</p>   
    
<p align="justify"> É a linguagem de programação nativa da web:</p>  

1. Importações de biblioteca padrão.
2. Importações de terceiros relacionados.
3. Importações específicas de aplicativos / bibliotecas locais.
Você deve colocar uma linha em branco entre cada grupo de importações.
    
    
<p align="justify">As importações absolutas são recomendadas, pois geralmente são mais legíveis e tendem a se comportar melhor (ou pelo menos fornecer mensagens de erro melhores) se o sistema de importação estiver configurado incorretamente (como quando um diretório dentro de um pacote termina em sys.path ):</p> 

```python
import mypkg.sibling
from mypkg import sibling
from mypkg.sibling import example
```

<p align="justify">No entanto, as importações relativas explícitas são uma alternativa aceitável às importações absolutas, especialmente ao lidar com layouts de pacotes complexos em que o uso de importações absolutas seria desnecessariamente prolixo:</p> 
    
```python
from . import sibling
from .sibling import example
``` 
    
 <p align="justify">O código da biblioteca padrão deve evitar layouts de pacote complexos e sempre usar importações absolutas. Ao importar uma classe de um módulo que contém uma classe, geralmente não há problema em soletrar o seguinte:</p>    
    
    
```python
from myclass import MyClass
from foo.bar.yourclass import YourClass
```    
    
 <p align="justify">Se essa grafia causar conflitos de nomes locais, soletre-os explicitamente:</p>       
    
 ```python
import myclass 
import foo.bar.yourclass
```    
  
 <p align="justify"> Importações de WildCard¹ ( de <module> import * ) devem ser evitadas, pois não deixam claro quais nomes estão presentes no namespace, confundindo os leitores e muitas ferramentas automatizadas. Há um caso de uso defensável para uma importação de WildCard, que é republicar uma interface interna como parte de uma API pública (por exemplo, sobrescrever uma implementação Python pura de uma interface com as definições de um módulo acelerador opcional e exatamente quais definições serão sobrescrito não é conhecido com antecedência). Ao republicar nomes dessa maneira, as diretrizes abaixo com relação às interfaces públicas e internas ainda se aplicam.</p>    

 <p align="justify"> ¹ O WildCard é um certificado de segurança SSL premium, ele possibilita a proteção de subdomínios ilimitados dentro de um único domínio através do protocolo HTTPS, em apenas um único certificado. </p> 
    
    
    

    

    
    
</p>
</details> 













  
