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

<p align="justify"> :robot: Também é possível analisar arquivos ". IPYNB", tendo em mente que o MotorHead tentará converter o nome do arquivo em um nome de módulo “.py” e só será capaz de processar o arquivo se for bem-sucedido. :robot: </p>



### Verificando arquivos

<p align="justify">:robot:  Uma modelo obrigatoriamente deverá possuir os arquivos README.md | requirements.txt | .gitignore , apenas com o conjunto desses arquivos será possível dar prosseguimento do modelo para a esteira de produção. Para a verificação em sua pasta de todos os atributos necessários é invocado o comando: :robot: </p>

~~~python
!python3 -m big_motorhead.cli -d
~~~

<p align="justify">:robot:  No caso da ausência de alguns dos arquivos será exibido uma mensagem de advertência da seguinte forma: :robot: </p>

```diff
Não foi encontrado os seguintes arquivos para validar a estrutura
```

```diff
README.md | requirements.txt | .gitignore 
```

<p align="justify">:robot:  No caso em que todos os requisitos sejam atendidos será exibido: :robot: </p>
    
```diff
+ PASSED                     100%
```

<p align="justify">:robot:  Para verificar a interpretação do seu código, bem como fornecer uma classificação geral com base no número e na gravidade dos erros é utilizado o comando: :robot: </p>


~~~python
!python3 -m big_motorhead.cli -f arquivos.ipynb
~~~

<p align="justify">:robot:  No caso do seu código esatr viavél de ser interpretado, bem como atendendo todos os requisitos supracitados você receberá um aviso: :robot: </p>

```diff
+ PASSED                     100%
```

<p align="justify">:robot:  Caso contrário uma advertência será exibida informando em qual linha encontra-se o "bug", bem como uma avaliação do seu código: :robot: </p>
    
 

```diff
- REJECT                      0%  
```



<h3 align="center">
    <a href="https://www.python.org/">🔗Boas Práticas</a>
</h3>

###
<details>
  <summary>Boas Práticas - Guia de estilo para código Python</summary>
    
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
    

### String Quotes
    
<p align="justify">Em Python, strings entre aspas simples e strings entre aspas são iguais. Este PEP não faz uma recomendação para isso. Escolha uma regra e cumpra-a. Quando uma string contém caracteres de aspas simples ou duplas, use o outro para evitar barras invertidas na string. Além disso, melhora a legibilidade.</p> 

    
### Espaço em branco em expressões e declarações
    
<p align="justify">Imediatamente entre parênteses, colchetes ou colchetes:</p>    
    
```python
# Correto:
spam(ham[1], {eggs: 2})
``` 
    
```python
# Errado:
spam( ham[ 1 ], { eggs: 2 } )
``` 
    
<p align="justify">Entre uma vírgula final e um parêntese de fechamento a seguir:</p>  

```python
# Correto:
foo = (0,)
``` 
    
```python
# Errado:
bar = (0, )
``` 
 
<p align="justify">Imediatamente antes de uma vírgula, ponto e vírgula ou dois pontos:</p>  
    
```python
# Correto:
if x == 4: print x, y; x, y = y, x
``` 
    
```python
# Errado:
if x == 4 : print x , y ; x , y = y , x
```     
    
<p align="justify">No entanto, em uma fatia, os dois pontos atuam como um operador binário e devem ter quantidades iguais em ambos os lados (tratando-o como o operador com a prioridade mais baixa). Em uma fatia estendida, os dois pontos devem ter o mesmo espaçamento aplicado. Exceção: quando um parâmetro de fatia é omitido, o espaço é omitido:</p>      
```python
# Correto:
ham[1:9], ham[1:9:3], ham[:9:3], ham[1::3], ham[1:9:]
ham[lower:upper], ham[lower:upper:], ham[lower::step]
ham[lower+offset : upper+offset]
ham[: upper_fn(x) : step_fn(x)], ham[:: step_fn(x)]
ham[lower + offset : upper + offset]
``` 
    
```python
# Errado:
ham[lower + offset:upper + offset]
ham[1: 9], ham[1 :9], ham[1:9 :3]
ham[lower : : upper]
ham[ : upper]
```    
 
<p align="justify">Imediatamente antes do parêntese de abertura que inicia a lista de argumentos de uma chamada de função:</p> 
    
```python
# Correto:
spam(1)
``` 
    
```python
# Errado:
spam (1)
```     

<p align="justify">Imediatamente antes do parêntese de abertura que inicia uma indexação ou fracionamento:</p>  
    
```python
# Correto:
dct['key'] = lst[index]
``` 
    
```python
# Errado:
dct ['key'] = lst [index]
```          
    
<p align="justify">Mais de um espaço ao redor de um operador de atribuição (ou outro) para alinhá-lo com outro:</p> 
    
```python
# Correto:
x = 1
y = 2
long_variable = 3
``` 
    
```python
# Errado:
x             = 1
y             = 2
long_variable = 3]
```   
    
### Outras Recomendações
     
<p align="justify">Evite espaços em branco à direita em qualquer lugar. Como geralmente é invisível, pode ser confuso: por exemplo, uma barra invertida seguida por um espaço e uma nova linha não conta como um marcador de continuação de linha. Alguns editores não o preservam e muitos projetos (como o próprio CPython) têm ganchos de pré-commit que o rejeitam.</p>

<p align="justify">Sempre rodeiam estes operadores binários com um único espaço em ambos os lados: de atribuição ( = ), atribuição ampliada ( + = , - = etc.), as comparações ( == , < , > , ! = , <> , <= , > = , in , not in , is , is not ), Booleanos ( e , ou , não ).</p>

<p align="justify">Se forem usados ​​operadores com prioridades diferentes, considere adicionar espaços em branco ao redor dos operadores com a (s) prioridade (s) mais baixa (s). Use seu próprio julgamento; no entanto, nunca use mais de um espaço e sempre tenha a mesma quantidade de espaços em branco em ambos os lados de um operador binário:</p>
    
```python
# Correto:
i = i + 1
submitted += 1
x = x*2 - 1
hypot2 = x*x + y*y
c = (a+b) * (a-b)
``` 
    
```python
# Errado:
i=i+1
submitted +=1
x = x * 2 - 1
hypot2 = x * x + y * y
c = (a + b) * (a - b)

```     

<p align="justify">As anotações de função devem usar as regras normais para dois pontos e sempre ter espaços ao redor da seta -> se houver. (Consulte as anotações de função abaixo para obter mais informações sobre as anotações de função.):</p>
    
```python
# Correto:
def munge(input: AnyStr): ...
def munge() -> PosInt: ...
``` 
    
```python
# Errado:
def munge(input:AnyStr): ...
def munge()->PosInt: ...
```      
<p align="justify">Não use espaços ao redor do sinal = quando usado para indicar um argumento de palavra-chave, ou quando usado para indicar um valor padrão para um parâmetro de função não anotado </p>    
    
```python
# Correto:
def complex(real, imag=0.0):
    return magic(r=real, i=imag)
``` 
    
```python
# Errado:
def complex(real, imag = 0.0):
    return magic(r = real, i = imag)
```    
 
<p align="justify">Ao combinar uma anotação de argumento com um valor padrão, no entanto, use espaços ao redor do sinal = :</p> 
    
```python
# Correto:
def munge(sep: AnyStr = None): ...
def munge(input: AnyStr, sep: AnyStr = None, limit=1000): ...
``` 
    
```python
# Errado:
def munge(input: AnyStr=None): ...
def munge(input: AnyStr, limit = 1000): ...
```     
    
<p align="justify">Instruções compostas (várias instruções na mesma linha) geralmente são desencorajadas:</p>    
    
```python
# Correto:
if foo == 'blah':
    do_blah_thing()
do_one()
do_two()
do_three()
``` 
    
```python
# Errado:
if foo == 'blah': do_blah_thing()
do_one(); do_two(); do_three()
```
    
<p align="justify">Embora às vezes seja normal colocar um if / for / while com um corpo pequeno na mesma linha, nunca faça isso para instruções com várias cláusulas. Além disso, evite dobrar essas linhas longas!</p>    
    
    
```python
# Muito Errado:
if foo == 'blah': do_blah_thing()
else: do_non_blah_thing()

try: something()
finally: cleanup()

do_one(); do_two(); do_three(long, argument,
                             list, like, this)

if foo == 'blah': one(); two(); three()
```

             
### Quando usar vírgulas finais
             
<p align="justify">As vírgulas finais são geralmente opcionais, exceto que são obrigatórias ao fazer uma tupla de um elemento. Para maior clareza, é recomendado colocar o último entre parênteses (tecnicamente redundantes):</p>        
    
```python
# Correto:
FILES = ('setup.cfg',)
```   
    
```python
# Errado:
FILES = 'setup.cfg',
```   
    
<p align="justify">Quando as vírgulas finais são redundantes, geralmente são úteis quando um sistema de controle de versão é usado, quando se espera que uma lista de valores, argumentos ou itens importados seja estendida ao longo do tempo. O padrão é colocar cada valor (etc.) em uma linha sozinho, sempre adicionando uma vírgula final e adicionar o parêntese / colchete / chave na próxima linha. No entanto, não faz sentido ter uma vírgula final na mesma linha do delimitador de fechamento (exceto no caso acima de tuplas de singleton):</p>      

```python
# Correto:
FILES = [
    'setup.cfg',
    'tox.ini',
    ]
initialize(FILES,
           error=True,
           )
```   
    
```python
# Errado:
FILES = ['setup.cfg', 'tox.ini',]
initialize(FILES, error=True,)
```  
 
### Comentários
    
<p align="justify">Comentários que contradizem o código são piores do que nenhum comentário. Sempre tenha como prioridade manter os comentários atualizados quando o código mudar! Os comentários devem ser frases completas. A primeira palavra deve ser maiúscula, a menos que seja um identificador que comece com uma letra minúscula (nunca altere a capitalização dos identificadores!).</p> 

<p align="justify">Os comentários em bloco geralmente consistem em um ou mais parágrafos construídos a partir de frases completas, com cada frase terminando em um ponto. Você deve usar dois espaços após um ponto final da frase em comentários com várias frases, exceto após a frase final. Certifique-se de que seus comentários sejam claros e facilmente compreensíveis para outros falantes do idioma em que você está escrevendo. Programadores Python de países que não falam inglês: por favor, escreva seus comentários em inglês, a menos que você tenha 120% de certeza de que o código nunca será lido por pessoas que não falam sua língua.</p>      
    
### Bloquear comentários
    
<p align="justify">Os comentários de bloco geralmente se aplicam a algum (ou todo) o código que os segue e são indentados no mesmo nível desse código. Cada linha de um bloco de comentário começa com um # e um único espaço (a menos que seja um texto recuado dentro do comentário). Os parágrafos dentro de um comentário de bloco são separados por uma linha contendo um único # .</p>     
    
### Comentários "Inline"

<p align="justify">Use comentários embutidos com moderação. Um comentário embutido é um comentário na mesma linha de uma declaração. Os comentários embutidos devem ser separados por pelo menos dois espaços da declaração. Eles devem começar com um # e um único espaço. Comentários inline são desnecessários e, na verdade, distraem se afirmam o óbvio. Não faça isso:.</p>
 
```python
#Errado
x = x + 1                 # Increment x
```   

    
### Convenções de Nomenclatura   

<p align="justify">As convenções de nomenclatura da biblioteca do Python são um pouco complicadas, então nunca vamos conseguir isso completamente consistente - no entanto, aqui estão os padrões de nomenclatura atualmente recomendados. Novos módulos e pacotes (incluindo estruturas de terceiros) devem ser escritos de acordo com esses padrões, mas onde uma biblioteca existente tem um estilo diferente, a consistência interna é preferida.</p>
    
    
#### Nomes a evitar    
<p align="justify">Nunca use os caracteres 'l' (letra el minúscula), 'O' (letra maiúscula oh) ou 'I' (olho de letra maiúscula) como nomes de variáveis ​​de caractere único. Em algumas fontes, esses caracteres são indistinguíveis dos numerais um e zero. Quando for tentado a usar 'l', use 'L'.</p>
    
#### Nomes de pacotes e módulos 
<p align="justify">Os módulos devem ter nomes curtos, todos em minúsculas. Sublinhados podem ser usados ​​no nome do módulo se melhorar a legibilidade. Os pacotes Python também devem ter nomes curtos, todos em minúsculas, embora o uso de sublinhados seja desencorajado. Quando um módulo de extensão escrito em C ou C ++ tem um módulo Python acompanhante que fornece uma interface de nível superior (por exemplo, mais orientada a objetos), o módulo C / C ++ tem um sublinhado inicial (por exemplo, _socket ).</p>    

    
#### Nomes de classes
<p align="justify">Os nomes das classes normalmente devem usar a convenção CapWords. A convenção de nomenclatura para funções pode ser usada em casos onde a interface é documentada e usada principalmente como um chamável. Observe que há uma convenção separada para nomes embutidos: a maioria dos nomes embutidos são palavras únicas (ou duas palavras executadas juntas), com a convenção CapWords usada apenas para nomes de exceção e constantes embutidas.</p>      

#### Nomes de Variáveis ​​Globais
<p align="justify">(Esperemos que essas variáveis ​​sejam destinadas ao uso em apenas um módulo.) As convenções são quase as mesmas que as das funções. Módulos que são projetados para uso por meio de M import * devem usar o mecanismo __all__ para evitar a exportação de globais ou usar a convenção mais antiga de prefixar esses globais com um sublinhado (o que você pode querer fazer para indicar que esses globais são "módulo não público "</p>       
    
#### Nomes de funções e variáveis
<p align="justify">Os nomes das funções devem estar em letras minúsculas, com palavras separadas por sublinhados, conforme necessário para melhorar a legibilidade. Os nomes das variáveis ​​seguem a mesma convenção dos nomes das funções. MixedCase é permitido apenas em contextos onde esse já é o estilo predominante (por exemplo, threading.py), para manter a compatibilidade com versões anteriores.</p>       

#### Argumentos de função e método
<p align="justify">Sempre use self como o primeiro argumento para métodos de instância. Sempre use cls para o primeiro argumento para métodos de classe. Se o nome de um argumento de função conflitar com uma palavra-chave reservada, geralmente é melhor anexar um único sublinhado final em vez de usar uma abreviatura ou erro ortográfico. Portanto, class_ é melhor do que clss . (Talvez seja melhor evitar esses confrontos usando um sinônimo.)</p>       
    
#### Nomes de métodos e variáveis ​​de instância
<p align="justify">Use as regras de nomenclatura de função: minúsculas com palavras separadas por sublinhados conforme necessário para melhorar a legibilidade. Use um sublinhado inicial apenas para métodos não públicos e variáveis ​​de instância. Para evitar conflitos de nome com subclasses, use dois sublinhados à esquerda para invocar as regras de mutilação de nome do Python. Python confunde esses nomes com o nome da classe: se a classe Foo tem um atributo denominado __a , ela não pode ser acessada por Foo .__ a . (Um usuário insistente ainda poderia obter acesso chamando Foo._Foo__a .) Geralmente, sublinhados à esquerda duplos devem ser usados ​​apenas para evitar conflitos de nome com atributos em classes projetadas para serem subclasses.</p>     
    
    
#### Constantes
<p align="justify">As constantes são geralmente definidas em um nível de módulo e escritas em letras maiúsculas com sublinhados separando as palavras. Os exemplos incluem MAX_OVERFLOW e TOTAL .</p>     
    
    
### Retorno

<p align="justify">Seja consistente nas declarações de retorno. Todas as instruções de retorno em uma função devem retornar uma expressão ou nenhuma delas. Se qualquer instrução de retorno retornar uma expressão, quaisquer instruções de retorno em que nenhum valor seja retornado devem declarar isso explicitamente como return None , e uma instrução de retorno explícita deve estar presente no final da função (se alcançável):</p>       
    
    
```python
# Correto:

def foo(x):
    if x >= 0:
        return math.sqrt(x)
    else:
        return None

def bar(x):
    if x < 0:
        return None
    return math.sqrt(x)
```   

  ```python
# Errado:

def foo(x):
    if x >= 0:
        return math.sqrt(x)

def bar(x):
    if x < 0:
        return
    return math.sqrt(x)
```   
   

</p>
</details> 













  
