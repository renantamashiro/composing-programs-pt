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





1.1.3   Interactive Sessions
In an interactive Python session, you type some Python code after the prompt, >>>. The Python interpreter reads and executes what you type, carrying out your various commands.

To start an interactive session, run the Python 3 application. Type python3 at a terminal prompt (Mac/Unix/Linux) or open the Python 3 application in Windows.

If you see the Python prompt, >>>, then you have successfully started an interactive session. These notes depict example interactions using the prompt, followed by some input.

>>> 2 + 2
4
Interactive controls. Each session keeps a history of what you have typed. To access that history, press <Control>-P (previous) and <Control>-N (next). <Control>-D exits a session, which discards this history. Up and down arrows also cycle through history on some systems.
## 1.2 Elementos da programação
## 1.3 Definindo novas funções
## 1.4 Elaborando funções
## 1.5 Controle
## 1.6 Funções de ordem superior
## 1.7 Funções recursivas
