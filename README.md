# Composing Programs - PT

> Tradução livre do conteúdo elaborado pelo John DeNero e disponível em https://www.composingprograms.com/


Seja bem-vindo ao Composing Programs, uma introdução gratuita para a programação e para a ciência da computação.

Na tradição do [SICP](http://mitpress.mit.edu/sicp/), este texto foca nos métodos para abstração, paradigmas da programação e técnicas para gerenciar a complexidade de grandes sistemas. Esses conceitos são ilustrados utilizando a linguagem de programação [Python 3](http://www.python.org/).

Em acréscimo a leitura dos capítulos abaixo, você pode praticar o conhecimento adquirido nos [projetos de programação](https://www.composingprograms.com/projects.html) que acompanham o texto e visualizar a execução do programa utilizando o [Online Python Tutor](https://www.composingprograms.com/tutor.html)

**Instrutores**: se você está interessando em adaptar qualquer um destes materiais para as suas aulas, por favor [preencha este formulário](https://docs.google.com/forms/d/1lcDf-_y9t1oSDH_-HFz3UhUFouAX1518XeCMnlRISss/viewform), assim podemos ajudar com os seus esforços.


**Capítulo 1: Construindo abstrações com funções**
* [1.1 Começando](#11-começando)
* [1.2 Elementos da programação](#12-elementos-da-programação)
* [1.3 Definindo novas funções](#13-definindo-novas-funções)
* [1.4 Elaborando funções](#14-elaborando-funções)
* [1.5 Controle](#15-controle)
* [1.6 Funções de ordem superior](#16-funções-de-ordem-superior)
* [1.7 Funções recursivas](#17-funções-recursivas)

**Capítulo 2: Construindo abstrações com dados**
* 2.1 Introdução
* 2.2 Abstração de dados
* 2.3 Sequências
* 2.4 Dados mutáveis
* 2.5 Programação orientada a objetos
* 2.6 Implementando classes e objetos
* 2.7 Abstração de objeto
* 2.8 Eficiência
* 2.9 Objetos recursivos

**Capítulo 3: Interpretando programas de computadores**
* 3.1 Introdução
* 3.2 Programação funcional
* 3.3 Exceções
* 3.4 Interpretadores para linguagens com combinação
* 3.5 Interpretadores para linguagens com abstração

**Capítulo 4: Processamento de dados**
* 4.1 Introdução
* 4.2 Sequências implícitas
* 4.3 Programação declarativa
* 4.4 Programação lógica
* 4.5 Unificação
* 4.6 Computação distribuída
* 4.7 Processamento de dados distribuído
* 4.8 Computação paralela


# Capítulo 1: Construindo abstrações com funções

## 1.1 Começando
Ciência da computação é uma disciplina acadêmica ampla. Ela contempla áreas de sistemas distribuídos, inteligência artificial, robótica, gráfica, segurança, computação científica, arquitetura de computadores e dezenas de subcampos emergentes que se expandem com novas técnicas e descobertas a cada ano. O rápido progresso da ciência da computação tem deixado poucos aspectos da vida humana sem alteração. Comércio, comunicação, ciência, arte, lazer e política foram todos reinventados como domínios computacionais.

A alta produtividade da ciência da computação é somente possível por conta do conjunto elegante e poderoso de ideias fundamentais em que a disciplina é construída. Toda computação começa representando informação, especificando lógica para processá-la e construindo abstrações que gerenciam a complexidade dessa lógica. Dominar esses fundamentos requer de nós entender precisamente como computadores interpretam programas de computadores e executam processos computacionais.

Essas ideais fundamentais vem sendo ensinadas por muito tempo pelo livro texto clássico _Structure and Interpretation of Computer Programs_ (SICP) pelo Harold Abelson e Gerald Jay Sussman com Julie Sussman. Este texto empresta fortemente as ideias do SICP, o qual os autores originais gentilmente licenciaram para adaptação e reuso com a licença Creative Commons. Essas notas foram publicadas com a licença de compartilhamento não comercial Creative Commons na versão 3.

### 1.1 Programação em Python

> Uma linguagem não é algo que você aprende, mas que você participa

Com o objetivo de definir processos computacionais, precisamos de uma linguagem de programação e de preferência uma que tanto humanos quanto uma grande variedade de computadores podem entender. Neste texto, vamos trabalhar primariamente com a linguagem Python.

Python é uma linguagem de programação amplamente utilizada que possui entusiastas recrutados de diferentes profissões: programadores web, engenheiros de jogos, cientistas, acadêmicos e até designers de novas linguagens de programação. Quando você aprende Python, você se junta a uma comunidade forte de milhões de desenvolvedores. Comunidades de desenvolvedores são instituições de extrema importância: membros ajudam uns aos outros para resolver problemas, compartilham projetos, experiências e desenvolvem software e ferramentas coletivamente. Membros dedicados frequentemente alcançam a celebridade e uma estima distribuída por suas contribuições.

A linguagem de programação Python em si é um produto de uma grande comunidade voluntária que se orgulha da diversidade de seus contribuidores. A linguagem foi concebida e implementada primeiramente por Guido Van Rossum  no final dos anos 80. O primeiro capítulo do tutorial dele sobre Python 3 explica a razão do Python ser tão popular, apesar da grande variedade de linguagens disponíveis atualmente.

Python se destaca como uma linguagem instrucional, pois, através de sua história, desenvolvedores Python tem enfatizado a interpretabilidade humana do código Python, reforçado pelos princípios de beleza, simplicidade e legibilidade do [Zen of Python](http://www.python.org/dev/peps/pep-0020/). Python é particularmente apropriada para este texto, uma vez que possui um amplo conjunto de recursos que oferece suporte a uma variedade de estilos de programação, o qual vamos explorar. Embora não exista uma forma única de se programar em Python, existe uma série de convenções compartihadas na comunidade de desenvolvedores que facilitam a leitura, compreensão e a extensão de programas existentes. A combinação de flexibilidade e acessibilidade do Python permite aos estudantes explorarem vários paradigmas de programação e, assim, aplicarem o conhecimento adquirido para milhares de projetos em andamento.

Estas notas mantém o espírito do SICP, introduzindo os recursos do Python com as técnicas de abstração e um rigoroso modelo computacional. Em acréscimo, estas notas fornecem uma introdução prática à programação em Python, incluindo alguns recursos avançados da linguagem e exemplos ilustrativos. O aumento da sua facilidade com o Python deve vir naturalmente conforme você avança no texto. 

O melhor caminho para começar à programação em Python é interagindo com o interpretador diretamente. Essa seção descreve como instalar o Python 3, iniciar uma sessão interativa com o interpretador e começar a programar.


### 1.1.2 Instalando Python 3
Como todo grande software, o Python possui várias versões. Este texto vai utilizar a versão estável mais recente do Python 3. Vários computadores possuem versões antigas do Python já instaladas como o Python 2.7, mas essas versões não vão corresponder as descrições deste texto. Você deve ser capaz de utilizar qualquer computador, mas espera-se a instalação do Python 3. (não se preocupe, Python é gratuito).

Você pode baixar o Python 3 na página de download clicando na versão que começa com 3 (não 2). Siga as instruções do instalador para completá-lo.

Para um guia mais detalhado, tente estes tutoriais de instalação no Windows e no Mac, criados pela Julia Oh.


### Sessoes interativas

Em uma sessão interativa de Python, você digita algum código Python após o _prompt_ _>>>_. O interpretador do Python lê e executa o que você digitou, executando seus vários comandos.

Para iniciar uma sessão interativa, rode a aplicação Python 3. Digite `python3` no _prompt_ do terminal (Mac/Unix/Linux) ou abra a aplicação Python 3 no Windows.

Se você ver o _prompt_ do Python (_>>>_), então você iniciou com sucesso uma sessão interativa. Estas notas mostram interações de exemplo utilizando o _prompt_, seguido de alguma entrada.

```
>>> 2 + 2
4
```

**Controles interativos**. Cada sessão mantêm um histórico do que foi digitado. Para acessar esse histórico, pressione `<Control>-P` (anterior) e `<Control>-N` (próximo). `<Control>-D` sai de uma sessão, o qual descarta todo o histórico. As setas para cima e para baixo também percorrem o histórico para alguns sistemas.


### 1.1.4 Primeiro Exemplo

Para dar uma introdução apropriada ao Python, nós vamos começar com um exemplo que utiliza diversos recursos da linguagem. Na próxima seção, começaremos do começo e comstruiremos a linguagem pedaço por pedaço. Pense nessa seção como uma prévia dos recursos que virão.

O Python possui suporte nativo para várias atividades comuns de programação, como: manipulação de texto, gráficos, comunicação na internet. O seguinte trecho de código Python:

```python
from urllib.request import urlopen
```

é uma sentença de importe que carrega a funcionalidade para acessar dados provenientes da internet. Em particular, deixa disponível a função chamada `urlopen` a qual pode acessar o conteúdo em um localizador uniforme de recurso (URL), uma localização de algo na internet.

**Sentenças e Expressões**. Código Python consiste de expressões e sentenças. Em termos gerais, programas de computadores consistem em instruções para:

1. Calcular algum valor
2. Realizar alguma ação

Sentenças normalmente descrevem ações. Quando o interpretador do Python executa uma sentença, ele realiza a ação correspondente. Por outro lado, expressões normalmente descrevem cálculos. Quando o Python avalia uma expressão, ele calcula o valor da expressão. Este capítulo introduz diversos tipos de sentenças e expressões.

A declaração da sentença:

```python
shakespeare = urlopen('http://composingprograms.com/shakespeare.txt')
```

associa o nome `shakespeare` com o valor da expressão que segue o sinal de igual `=`. Essa expressão aplica a função `urlopen` para a URL que contêm o texto completo das 37 peças de William Shakespeare, tudo em um único documento de texto.

**Funções**. Funções encapsula lógica que manipula dados. `urlopen` é uma função. Um endereço Web é um pedaço de dados e o texto das peças de Shakespeare é outro. Mas nós podemos aplicar esse processo utilizando somente uma simples expressão, uma vez que a complexidade dessa operação é tratada pela função. Funções é o principal tópico deste capítulo.

Outra sentença de atribuição

```python
words = set(Shakespeare.read().decode().split())

```

associa o nome `words` para o conjunto de todas as palavras únicas que aparecem nas peças de Shakespeare, todas as 33.721. A corrente de comandos para ler, decodificar e separar operam em uma entidade computacional intermediária: nós lemos o dado da URL aberta, então decidi ficamos o dado para texto e finalmente separamos o texto em palavras. Todas essas palavras são organizadas no conjunto.

**Objetos**. O conjunto é um tipo de objeto, o qual suporta operações de conjunto como cálculo de interseção e união. Um objeto agrupa de forma transparente dados e a lógica que manipula esses dados, de modo que gerencia a complexidade de ambos. Objetos são o tópico principal do Capítulo 2. Finalmente, a expressão 

```python
{w for w in word if len(w) == 6 and w[::-1] in words}
{'redder', 'drawer', 'reward', 'diaper', 'repaid'}
```
é uma expressão composta que avalia para o conjunto de todas as palavras Shakespearianas que também são uma palavra caso soletrada ao contrário. A notação enigmática `w[::-1]` avalia cada letra em uma palavra, mas o `-1` manda dar um passo para trás. Quando você digita uma expressão em uma sessão interativa, o Python exibe o valor da expressão na linha seguinte.

**Interpretadores**: Avaliar expressões compostas requer um procedimento preciso que interpreta código de um modo previsível. Um programa que implementa este tipo de procedimento, avaliando expressões compostas, é chamado de um interpretador. O design e implementação de interpretadores é o principal tópico do Cappítulo 3.

Quando comparado com outros programas de computadores, interpretadores para linguagens de programação são únicos em sua generalização. Python não foi construído com Shakespeare em mente. No entanto, sua grande flexibilidade nos permitiu processar uma grande quantidade de texto com poucas sentenças e expressões.

No final, nós vamos achar que todos estes conceitos centrais são extremamente relacionados: funções são objetos, objetos são funções e interpretadores são instâncias de ambos. No entanto, desenvolver um entendimento claro de cada um desses conceitos e seus pápeis na organização do código é crítico para dominar a arte da programação.

### 1.1.5 Erros

Python está esperando pelo seu comando. Você está encorajado de experimentar a linguagem, mesmo sem saber todo o seu vocabulário e estrutura. Mas, esteja preparado para erros. Apesar de computadores serem rápidos e flexíveis, eles são extremamente rígidos. A natureza dos computadores está descrita no curso introdutório da Universidade de Stanford como:

A equação fundamental de computadores é:

computador = poderoso + estúpido

Os computadores são muito poderosos, processando altos volumes de dados bem rapidamente. Os computadores podem processar bilhões de operações por segundo, em que cada operação é bastante simples.

Os computadores são também chocantemente estúpidos e frágeis. As operações que eles conseguem fazer são extremamente rígidos, simples e mecânicos. O computador não tem um entendimento real... não é nada como o HAL 9000 dos filmes. No mínimo, você não deve ficar intimidado por um computador como se ele tivesse algum tipo de cérebro. É muito mecânico por baixo de tudo.

Programação é sobre a pessoa utilizar seu conhecimento real para construir algo útil, construído a partir dessas pequenas e simples operações que o computador pode fazer.

A rigidez dos computadores ficarão aparentes conforme você utilizar o interpretador do Python: até mesmo pequenos mudanças de ortografia e formatação vão causar inesperadas saídas e erros.

Aprender a interpretar erros e diagnosticar a causa de erros inesperados é chamado de depuração. Alguns princípios orientadores de depuração são:

1. Testar de forma incremental: Todo código bem escrito é composto de pequenos componentes modulares que podem ser testados individualmente. Teste tudo que você escreve o mais cedo possível para identificar problemas o quanto antes e ganhe confiança de seus componentes.
2. Isolar erros: Um erro em uma saída de uma sentença pode tipicamente ser atribuído para um componente modular específico. Quando tentar diagnosticar um problema, trace o erro para o menor fragmento de código antes de corrigí-lo.
3. Verifique as suas hipóteses: Interpretadores executam as suas instruções ao pé da letra - sem mais nem menos. A sua saída é inesperada quando o comportamento de algum código não corresponde ao o que o programador esperava (ou assumiu). Conheça as suas hipóteses e então foque o esforço da sua depuração em verificar que as suas hipóteses se mantêm.
4. Consulte outras pessoas: Você não está sozinho! Se você não entender uma mensagem de erro, pergunte para um amigo, instrutor ou no mecanismo de busca. Se você isolou um erro, mas não consegue descobrir como corrigí-lo, pergunte para alguém para dar uma olhada. Um monte de conhecimento valioso de programação é compartilhado em um processo de resolução de problemas em grupo.

Teste incremental, design modular, hipóteses precisas e trabalho em equipe são temas que persistem neste texto. Espera-se que todos persistam na sua carreira em ciência da computação.


## 1.2 Elementos da programação
## 1.3 Definindo novas funções
## 1.4 Elaborando funções
## 1.5 Controle
## 1.6 Funções de ordem superior
## 1.7 Funções recursivas
