![Logo da FEUP](http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png)

# _Hextris_ - A fast paced HTML5 game inspired by Tetris!

![Logo do Hextris](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/favicon.ico)

## Descrição do Projeto

O Hextris é um simples e acessível jogo de puzzle, criado nas linguagens Javascript e HTML5 Canvas. Toma como inspiração os clássicos jogos arcade _Tetris_ e _QbQbQb_. Pode ser jogado em browser, no computador ou ainda em versão móvel, num smartphone ou num tablet (IOS ou Android).

O objetivo do jogo é similar ao do Tetris: evitar que os blocos coloridos atinjam a zona crítica, delimitada por um hexágono cinzento.
No hexágono central, a azul, é mostrada a pontuação atual do jogador.

À medida que o jogo progride, blocos coloridos caem da zona exterior aos hexágonos, para dentro da área de jogo. Ao chegarem ao hexágono central ou a qualquer outro bloco em cima deste, o bloco é empilhado nesse lado do hexágono e cola-se a este, girando com ele.
A pilha vai aumentando sempre que lhe é adicionada uma peça, até chegar à altura limite.
A velocidade com que os blocos caem não é constante, e não cai sempre apenas um bloco ao mesmo tempo.

Colocar três ou mais blocos da mesma cor numa situação de adjacência elimina-os da área de jogo e atribui pontuação ao jogador. Eliminar blocos começa um combo, que por sua vez aumenta pontuação que seria normalmente atribuida por eliminar blocos. O combo tem um tempo limitado, apresentado na barra que aparece na parte exterior do hexágono cinzento.

O jogador controla o hexágono central com as setas do teclado, na versão de browser. Na versão móvel, controla-o tocando nos lados esquerdo ou direito do ecrã, e pode ainda tocar no hexágono central para aumentar ou diminuir a velocidade de jogo.

## Software development process

Este jogo foi desenvolvido ao longo de 2 anos por 4 estudantes de uma escolar secundária, com idades que variam dos 15 anos aos 17 anos. A fase inicial do projeto foi criada no âmbito de um evento Hackathon e data de 11 de Maio de 2014. Esta iniciativa serve como uma congregação de programadores, designers e outros tipos de profisisonais ligados às áreas de desenvolvimento de software e informática que tem como objectivo a criação de uma aplicação/software totalmente usável, para fins recriacionais.

Contactámos o contribuidor principal do projecto e foi-nos informado que ao longo do desenvolvimento do projecto não foi considerada nenhuma estratégia ou processo de desenvolvimento de software (uma separação de desenvolvimento em fases distintas, contendo atividades com a função de tornar mais fácil o planeamento e gestão do projecto em cause).

No entanto, pela análise dos commits na página Github da aplicação, observamos que esta foi maioritariamente desenvolvida durantes os primeiros meses desde a sua conceção, com ocasionais mas notavelmente inferiores picos de atividade durante os próximos dois anos.

Através destes fatos e tendo em conta a natureza dos eventos do tipo no qual a Hackathon se insere e as ferramentas usadas na organização do projecto (nomeadamente o website Trello, que funciona como um método simples e flexível de gerir qualquer tipo de projecto, através de uma interface semelhante a um tabuleiro, no qual várias tarefas a serem realizadas podem ser afixadas para que possam ser geridas e implementadas por vários contribuidores e o Github), chegámos á conclusão que foi usado o processo de desenvolvimento "Iterative and Incremental Development".

"Iterative and Incremental Development" é uma estratégia de planeamento em que várias partes do software são desenvolvidas em paralelo, e integradas quando completas.

![Commits do Hextris](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/Commits.PNG)

## Hextris foi criado por:
* [Logan Engstrom](http://loganengstrom.com/)
* [Garret Finucane](http://garrettdreyfus.github.io/)

### Relatório elaborado por:
* Gonçalo Ribeiro, _
* Nuno Corte-Real, 	up201405158@fe.up.pt
* Nuno Martins, 	up201405079@fe.up.pt
* Rui Soares,		up201404965@fe.up.pt
