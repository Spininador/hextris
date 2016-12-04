![Logo da FEUP](http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png)

# [_Hextris_](https://github.com/Hextris/hextris) - A fast paced HTML5 game inspired by Tetris!

![Logo do Hextris](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/favicon.ico)

# 1. Introdução
Como complemento aos relatórios anteriores sobre o projeto _Hextris_, foi-nos proposta a análise e consequente elaboração do relatório da vertente de testabilidade do projeto em questão. Em contraste às propostas anteriores, esta implica uma cuidadosa leitura do código-fonte, e dos testes nele presentes, para poder inferir sobre o grau de testabilidade do código, a cobertura de testes, etc.
Para além disto, depois da análise de testes do software foi-nos sugerido também encontrar e corrigir um _bug_, e relatar este processo neste documento.

# 2. Testablidade de Software
A avaliação da testabilidade do software é crucial para garantir que mantém a sua integridade e qualidade como produto final. Assim, quer-se o maior grau de testabilidade possível, para garantir que todos os módulos ou componentes do projeto estão bem testados, seja em quantidade de testes como na sua qualidade.
A falta de testes no projeto pode levar a não serem detetados _bugs_ importantes que detêm o utilizador final da experiência completa (e correta) do produto. Cabe então ao(s) _developer(s)_ (e neste caso, como o projeto é _open-source_, qualquer utilizador disposto a tal), construir toda a heurística de testes para o software, e otimizar a sua coerência e qualidade.

É de notar que a testabilidade do software é algo que varia conforme a sua escala, complexidade, objetivo, etc., e ainda da plataforma e política de testes nele empregue.

No tipo de projeto que temos em análise, um jogo, a testabilidade é algo difícil de analisar. Por um lado, sendo fácil testar modularmente o motor de jogo, é difícil conceber casos de teste para todos os estados possíveis de jogo. Para além disso, é um desafio testar a parte visual do projeto.

Como no projeto em causa não são realizados quaisquer testes, para fazermos esta análise de testes decidimos analisar quais seriam os melhores caminhos a tomar para garantir a boa testabilidade de software em cada um dos seus vetores.

## 2.1. Controlabilidade
A controlabilidade dos testes é definida como o grau de controlo dos componentes sob teste (CUT) em relação ao teste. Isto implica que uma maior controlabilidade de testes é obtida quanto mais flexíveis forem as estruturas a serem testadas.
Assim, o objetivo é que o objeto a ser testado não seja demasiado específico para um estado em concreto, mas sim flexível para vários estados do ambiente de teste.

Para o projeto em questão, seria importante a realização de testes unitários sobre os componentes de jogo, no módulo do motor de jogo. No entanto, é visível aqui um problema: muitas das propriedades dos objetos estão _hard-coded_, ou seja, definidos apenas dentro do corpo das funções, sendo que isto limita significativamente a manipulação destes objetos. Para além disto, alguns dos seus comportamentos estão interdependentes, ou seja, para testar alguns componentes é necessário fornecer um ambiente de teste já com outros objetos, ou seja, bastante específico. Damos aqui o exemplo dos blocos, que dependem da posição do hexágono central, e a sua posição final depende da deste último. 

Vem então que a controlabilidade seria bastante limitada pela forma como estão definidos estes componentes, pelo que sugeríamos uma melhor parametrização destes, de forma a torná-los mais flexíveis para ambientes de jogo diferentes.

## 2.2. Observabilidade
A observabilidade de testes demonstra quão facilmente os resultados (intermédios e/ou finais) dos testes realizados são passíveis de serem observados.

Isto implica ser possível de ver todos os passos que levaram ao resultado final do teste, e idealmente poder ser feito um _backtracking_ da execução do teste. Isto ajuda a compreender todo o mecanismo de execução do mesmo, e ajuda a isolar o que poderá ter corrido mal.
Para além disto, uma boa observabilidade geral deve ser acompanhada de ferramentas externas que analisam e mostram as estatísticas de teste para qualquer um dos testes em análise. No entanto, o objetivo é que o _developer_ consiga, olhando para os testes, perceber exatamente o que está a acontecer em cada passo.
Para além disto tudo, há que notar que a parte visual do software, ou seja, tudo o que implica renderização, é de observabilidade excecionalmente fácil, já que uma falha nesta implica uma renderização bizarra ou não desejada.

## 2.3. _Isoleability_
A avaliação do fator de _isoleability_ envolve compreender quão facilmente é testar, isoladamente, cada componente sob teste (CUT).

Num projeto deste tipo, quão melhor é este fator mais modular e manipulável é cada componente, independentemente do ambiente de teste aplicado. Assim, quer-se que cada componente seja uma entidade independente, pelo que quaisquer dependências de ferramentas de outros componentes diminui este fator. Já foi referido em 2.1., mas reiteramos neste ponto que há componentes que apresentam dependência de atributos/funções de outros componentes, e como tal, testar um implica introduzir no ambiente de teste o outro também.

## 2.4. Separação de preocupações
Na área de ciência da computação, entende-se por "separação de preocupações" o protocolo de separarar as várias componentes de um programa em várias partes, de modo a que cada uma delas seja responsável por uma unção diferente, mais especializada. Por "preocupação" entende-se todos os detalhes do hardware em função do qual o código é otimizado.

Quando o princípio da separação de preocupações é implementado de uma maneira pertinente, as várias secções individuais do programa podem ser re-utilizadas, assim como desenvolvidas e atualizadas de uma forma fácil e independente. Torna-se também mais eficiente a distribuição destas tarefas por vários elementos da equipa de implementação do projeto.

Apesar de ser desenvolvido em JavaScript, uma linguagem que não está otimizada à progamação orientada por objetos (um paradigma de programação que é bastante compatível com o uso do conceito de separação de preocupações, o código e as suas funções foi repartido em várias secções especializadas, através de uma simulação da já mencionada programação orientada por objetos (nomeadamente, através da criação de objetos que funcionam como classes e se articulam entre si). 

De acordo com a informação supracitada, podemos inferir que o programa em questão foi desenvolvido de forma a maximizar a sua futura gestão e flexibilidade, princípios intrinsicamente relacionados com o princípio da separação de preocupações, sendo portanto este princípio adequadamente implementado no âmbito do desenvolvimento do código do projeto.


## 2.5. Compreensabilidade
Este critério avalia a maneira como o código do programa está documentado e a sua compreensabilidade/elegibilidade em si mesmos. Deste modo, consideram-se boas práticas de compreensabilidade uma documentação explícita, informativa, simples e bem apresentada do código, assim como um código que seja intuitivamente perceptível e também bem apresentado.
No projeto em questão, a documentação é bastante rudimentar. Os únicos comentários que o código apresenta são ocasionais esclarecimentos de certos raciocínios específicos ao programa. No entanto, o código é bem apresentado, organizado e as variáveis utilizadas possuem nomes pertinentes e adequados às suas respetivas funções. Conclui-se assim que apesar de a documentação ser bastante reduzida, devido à escala e natureza casual do projeto esta é adequada.

## 2.6. Heterogeneidade
Este critério aborda a maneira e facilidade de se efetuarem em paralelo diversos testes ao programa, através do uso de uma miríade de métodos, ferramentas e tecnologias. Como o Hextris é um projeto open-source, onde qualquer um pode contribuir através do Github, são essenciais testes que permitam garantir um bom funcionamento constante do programa, testes esses feitos a partir de tecnologias compatíveis com a linguagem utilizada para desenvolver o projeto (JavaScript).

# 3. Estatísticas de teste
As estatísticas de teste referem-se a uma interpretação e análise dos vários testes e consequente intercalação no código do projeto. Pela análise ao repositório Github do projeto e ao seu código podemos concluir que não se verifica a existência de quaisquer testes. Devido à pequena escala do projeto, seu funcionamento simples e relativo pequeno número de contribuidores (11, no total), a não existência de testes não é muito importante.

## 3.1 Métricas de _software_
Recorrendo ao pacote _complexity-report_ do _Node.js_ como ferramenta de análise estática, foi possível obter várias métricas do código deste projecto, de entre as quais a *complexidade ciclomática* (ou *de _McCabe_*) - medição dos caminhos de execução independentes dentro do código. Esta métrica constitui um bom indicador da complexidade de cada função. Quanto maior for o valor de complexidade, maior é a probabilidade da existência de _bugs_. Como regra geral, um _developer_ tenta sempre programar métodos que não excedam um valor padrão de complexidade (usualmente 5 ou 10). Para além disso, esta métrica também permite antecipar o número mínimo de testes necessários para se obter uma cobertura total do código - por exemplo - um método com um valor de complexidade 5 tem 5 ramificações de execução possíveis, e portanto são necessários pelo menos 5 testes (1 teste por ramificação) para se testar a integridade da sua cobertura.

Este é o resumo do relatório gerado pelo  _complexity-report_:
>
# Complexity report, 2016-12-4
* Mean per-function logical LOC: 15.331397196559783
* Mean per-function parameter count: 1.2799371197754466
* Mean per-function cyclomatic complexity: 4.917306306580604
* Mean per-function Halstead effort: 22600.797090637363
* Mean per-module maintainability index: 98.90721430081634
* First-order density: 0%
* Change cost: 7.142857142857142%
* Core size: 0%

A complexidade média de cada função é apróximadamente 5, resultado considerado bastante bom. Sabendo que existem 123 funções neste projecto, no mínimo 615 testes teríam que ser escritos para se obter cobertura total. Existem ainda algumas funções que consideramos serem boas candidatas a _refactoring_, por apresentarem um nível de complexidade elevado:

| Método        | Complexidade  | Módulo    |
| :-----------: |:-------------:| :--------:|
| render()      | 19            | render.js |
| init()        | 18            | main.js   |
| animLoop()    | 18            | main.js   |

# 4. Identificação de um _bug_ e correção

Devido à pequena escala do projeto, é difícil encontrar bugs, no entanto, foi identificado um "pequeno grande" bug, já que este pode causar que jogo ficar invisível, mas a sua correção foi bastante rápida.

## 4.1. Descrição do _bug_

Quando uma peça aterra no Hex central, é chamada a função shake(), que faz o Hex central, em conjunto com todas as peças anteriormente colocadas, abanarem numa certa direção.
Este abalo tem uma magnitude extremamente baixa, quase não percetível.No entanto, algumas vezes, este seria tao forte que faria a Hex sair da área de jogo, e por vezes até do ecrã e nunca mais voltar.

![Bug](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/bug.PNG)

Na imagem pode-se observar a Hex central a afastar-se do centro, algo que não deveria acontecer.

## 4.2. Causa do _bug_

O bug está na função shake(), em Hex.js , linha 35, que recebe _magnitude_ como parâmetro, movendo a Hex na direção pretendida numa distância proporcional a _magnitude_.
Depois de a nova posição da Hex ser calculada a partir de _magnitude_, o valor desta variável é decrementado, para que o abalo na próxima iteração seja menor, até que pára quando o valor de _magnitude_ for menor que 1.
O problema está na função usada para realizar a decrementação de _magnitude_, que é: "_obj.magnitude /= 2 * this.dt;_".
Na maior parte dos dispositivos usados para jogar, e possívelmente no disposítivo usado pelo _developer_, _this.dt_, que representa a variação de tempo desde a iteração anterior, toma valores superiores a 0,5.
No entanto, foi possível observar que nalguns casos, o valor de _this.dt_ tomaria valores menores que 0,5.Isto leva a que o novo valor de _magnitude_ seja dividido por um valor menor que 1, e, por isso, incremente.
Já que o _offset_ da peça central durante o abalo é calculado a partir de _magnitude_, quando esta aumenta, o _offset_ aumentará também infinitamente.

## 4.3. Correção do _bug_

A correção do bug foi feita ao alterar a linha "_obj.magnitude /= 2 * this.dt;_" para "_obj.magnitude = (obj.magnitude / 2) * this.dt;_".Assim, _this.dt_ é multiplicado no numerador e não no denominador, não podendo assim o valor de magnitude aumentar.

## 4.4. Pull Request

Foi criado um novo branch chamado "_esof\_bugfix_" , no qual foi corrigido o _bug_ enunciado, e, posteriormente, efetuado um _pull request_ para o fork/branch principal.

### Relatório elaborado por:

* [Gonçalo Ribeiro](https://github.com/gribeirofeup),  goncalo.ribeiro@fe.up.pt - 25%
* [Nuno Corte-Real](https://github.com/nunocr), 	up201405158@fe.up.pt - 25%
* [Nuno Martins](https://github.com/Spininador), 	up201405079@fe.up.pt - 25%
* [Rui Soares](https://github.com/RuiCS),		up201404965@fe.up.pt - 25%

<!-- 
Assignment 4: Verification and Validation
The goal of this fourth assignment is to document the project according to the current state with respect to verification and validation. This assignment requires you to carefully and thoroughly inspect the source code. You're also free to choose (static/dynamic) testing tools to help you test and debug and project. 

In particular, this report should discuss the following

Discuss Software Testability and Reviews: controllability, observability, isolateability, separation of concerns, understandability, heterogeneity.  
Grade: 6pts
Report Test Statistics and analytics:  e.g., number of test cases, percentage of coverage, number of flaky tests, etc. (see links of projects in moodle for inspiration)
Grade: 8pts
Identify a new bug and/or correct a bug
Grade: 6pts (identification: 4 points; correction: 2 points)
You think your project has no bugs?! Then, you do need to have a compelling story for us to credit you 6pts! 

-->
