![Logo da FEUP](http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png)

# [_Hextris_](https://github.com/Hextris/hextris) - A fast paced HTML5 game inspired by Tetris!

![Logo do Hextris](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/favicon.ico)

# 1. Introdução
Como complemento aos relatórios anteriores sobre o projeto _Hextris_, foi-nos proposta a análise e consequente elaboração do relatório da vertente de testabilidade do projeto em questão. Em contraste às propostas anteriores, esta implica uma cuidadosa leitura do código-fonte, e dos testes nele presentes, para poder inferir sobre o grau de testabilidade do código, a cobertura de testes, etc.
Para além disto, depois da análise de testes do software foi-nos sugerido também encontrar e corrigir um _bug_, e relatar este processo neste documento.

# 2. Testablidade de Software
A avaliação da testabilidade do software é crucial para garantir que mantém a sua integridade e qualidade como produto final. Assim, quer-se o maior grau de testabilidade possível, para garantir que todos os módulos ou componentes do projeto estão bem testados, seja em quantidade de testes como na sua qualidade.
A falta de testes no projeto pode levar a não serem detetados _bugs_ importantes que detêm o utilizador final da experiência completa (e correta) do produto. Cabe então ao(s) _developer(s)_ (e neste caso, como o projeto é _open-source_, qualquer utilizador disposto a tal), construir toda a heurística de testes para o software, e otimizar a sua coerência e qualidade.

No tipo de projeto que temos em análise, um jogo, a testabilidade é algo difícil de analisar. Por um lado, sendo fácil testar modularmente o motor de jogo, é difícil conceber casos de teste para todos os estados possíveis de jogo. Para além disso, é um desafio testar a parte visual do projeto.

## 2.1. Controlabilidade
## 2.2. Observabilidade
## 2.3. _Isoleability_
## 2.4. Separação de preocupações
## 2.5. Compreensabilidade
## 2.6. Heterogeneidade
# 3. Estatísticas de teste
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
A correção do bug foi feita ao alterar a linha "_obj.magnitude /= 2 * this.dt;_" para "_obj.magnitude -= 2 * this.dt;_".Assim, mesmo que o valor de _this.dt_ seja inferior a 0,5 , não haverá problemas, pois a decrementação será constante.
## 4.4. Pull Request
Foi criado um novo branch chamado "_esof\_bugfix_" , no qual foi corrigido o _bug_ enunciado, e, posteriormente, efetuado um _pull request_ para o fork/branch principal.
### Relatório elaborado por:
* [Gonçalo Ribeiro](https://github.com/gribeirofeup),  goncalo.ribeiro@fe.up.pt - %
* [Nuno Corte-Real](https://github.com/nunocr), 	up201405158@fe.up.pt - %
* [Nuno Martins](https://github.com/Spininador), 	up201405079@fe.up.pt - %
* [Rui Soares](https://github.com/RuiCS),		up201404965@fe.up.pt - %

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
