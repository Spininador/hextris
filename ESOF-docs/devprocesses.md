![Logo da FEUP](http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png)

# [_Hextris_](https://github.com/Hextris/hextris) - A fast paced HTML5 game inspired by Tetris!

![Logo do Hextris](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/favicon.ico)

## 1. Descrição do Projeto

O Hextris é um simples e acessível jogo de puzzle, criado nas linguagens Javascript e HTML5 Canvas. Toma como inspiração os clássicos jogos arcade _Tetris_ e _QbQbQb_. Pode ser jogado em browser, no computador ou ainda em versão móvel, num smartphone ou num tablet (IOS ou Android).

O objetivo do jogo é similar ao do Tetris: evitar que os blocos coloridos atinjam a zona crítica, delimitada por um hexágono cinzento.
No hexágono central, a azul, é mostrada a pontuação atual do jogador.

À medida que o jogo progride, blocos coloridos caem da zona exterior aos hexágonos, para dentro da área de jogo. Ao chegarem ao hexágono central ou a qualquer outro bloco em cima deste, o bloco é empilhado nesse lado do hexágono e cola-se a este, girando com ele.
A pilha vai aumentando sempre que lhe é adicionada uma peça, até chegar à altura limite.
A velocidade com que os blocos caem não é constante, e não cai sempre apenas um bloco ao mesmo tempo.

Colocar três ou mais blocos da mesma cor numa situação de adjacência elimina-os da área de jogo e atribui pontuação ao jogador. Eliminar blocos começa um combo, que por sua vez aumenta pontuação que seria normalmente atribuida por eliminar blocos. O combo tem um tempo limitado, apresentado na barra que aparece na parte exterior do hexágono cinzento.

![Imagem do jogo](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/gameexample.PNG)

O jogador controla o hexágono central com as setas do teclado, na versão de browser. Na versão móvel, controla-o tocando nos lados esquerdo ou direito do ecrã, e pode ainda tocar no hexágono central para aumentar ou diminuir a velocidade de jogo.

Hextris pode ser jogado em [hextris.io](http://hextris.io).
O repositório do projeto encontra-se em: [https://github.com/Hextris/hextris](https://github.com/Hextris/hextris)

## 2. Desenvolvimento do Projecto

### 2.1. Objetivo e Contexto do Projeto

Este jogo foi desenvolvido ao longo de 2 anos por 4 estudantes de uma escola secundária, com idades que vão dos 15 anos aos 17 anos. A fase inicial do projeto foi criada no âmbito de um evento Hackathon e data de 11 de Maio de 2014. Esta iniciativa serve como uma congregação de programadores, designers e outros tipos de profissisonais ligados às áreas de desenvolvimento de software e informática e tem como objectivo a criação de uma aplicação/software totalmente usável, para fins recreacionais.

### 2.2. Processo de Software

Como sugerido para a primeira fase da nossa análise ao projeto, contactámos um dos contribuidores principais deste, a fim de sabermos se foi ou não considerado um processo de desenvolvimento em concreto para o planeamento (e eventual gestão) do projeto em causa. Foi-nos informado que não foi considerada nenhuma estratégia ou processo de desenvolvimento do software antecipadamente ou durante a sua elaboração.

No entanto, pela análise dos commits na página Github da aplicação, observámos que esta foi maioritariamente desenvolvida durantes os primeiros meses desde a sua conceção, com ocasionais mas notavelmente inferiores picos de atividade durante os próximos dois anos.

![Commits do Hextris](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/Commits.PNG)

Através destes factos e tendo em conta a natureza dos eventos do tipo no qual a Hackathon se insere e as ferramentas usadas na organização do projecto (nomeadamente o website Trello, que funciona como um método simples e flexível de gerir qualquer tipo de projecto, através de uma interface semelhante a um tabuleiro, no qual várias tarefas a serem realizadas podem ser afixadas para que possam ser geridas e implementadas por vários contribuidores e o Github), chegámos à conclusão que foi usado o processo de desenvolvimento "Iterative and Incremental Development".

"Iterative and Incremental Development" é uma estratégia de planeamento em que várias partes do software são desenvolvidas em paralelo, e integradas quando completas.

### 2.3. Principais Contribuições e Política Open-source

Como projeto desenvolvido por estudantes, estes são os principais contribuidores. São, nomeadamente:
* [Logan Engstrom](https://github.com/lengstrom)
* [Garret Finucane](https://github.com/garrettdreyfus)
* [Noah Moroze](https://github.com/nmoroze)
* [Michael Yang](https://github.com/themichaelyang)

No entanto, como foi adotada a política open-source, qualquer utilizador pode propôr mudanças e melhorias. Isto garante que o projeto seja constantemente atualizado e testado, e torna fácil obter feedback constante da comunidade, seja em corrigir potenciais bugs, seja adicionar elementos ao jogo.

### 2.4. Testing

Todo o controlo de testes e correção de bugs é feito pela equipa principal do projeto, mas qualquer utilizador pode testar e modificar o código, e solidificá-lo contra potenciais bugs que tenha identificado.

## 3. Análise Crítica
### 3.1 Escolha de Estratégia
Visto que este projecto foi realizado no âmbito de uma competição, onde o tempo de concepção tem que ser encarado com um recurso limitado, consideramos adequado o emprego de um processo iterativo de desenvolvimento.

Efectivamente, neste tipo de estratégia de planeamento, a estrutura do projecto tende a degradar à medida que novos incrementos vão sendo implementados, inferindo-se que é mais indicada para projectos de pequena dimensão, produzidos num curto espaço de tempo, tal como é o caso.

Para além do que já foi referido, este proceso de *software* permite obter um protótipo funcional nas etapas iniciais de desenvolvimento e minimizar o risco do aparecimento de obstáculos insperados ao nivel da implementação.

### 3.2. Estrutura do Repositório
O projecto tem vários *branches*, mas nenhum se encontra activo de momento, com excepção do [*gh-pages*](https://github.com/Hextris/hextris/tree/gh-pages) (*default branch*) que hospeda o último *release* do jogo.

A estrutura do repositório segue o *Git Branching Model*, contendo dois *branches* principais paralelos, [*dev*](https://github.com/Hextris/hextris/tree/dev) e [*master*](https://github.com/Hextris/hextris/tree/master), e um conjunto de *supporting branches* onde cada colaborador implementa novos incrementos que vão sendo fundidos de volta ao *dev*.

### Relatório elaborado por:
* [Gonçalo Ribeiro](https://github.com/gribeirofeup),  goncalo.ribeiro@fe.up.pt - 25%
* [Nuno Corte-Real](https://github.com/nunocr), 	up201405158@fe.up.pt - 25%
* [Nuno Martins](https://github.com/Spininador), 	up201405079@fe.up.pt - 25%
* [Rui Soares](https://github.com/RuiCS),		up201404965@fe.up.pt - 25%
