![Logo da FEUP](http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png)

# [_Hextris_](https://github.com/Hextris/hextris) - A fast paced HTML5 game inspired by Tetris!

![Logo do Hextris](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/favicon.ico)

## 1. Introdução
O presente relatório visa a análise da *Arquitetura de _Software_* empregue no desenvolvimento do *Hetris*. Pretendemos identificar e criticar os diferentes _arquitectural patterns_ que possam estar a ser utilizadoes, assim como analisar este projecto à luz do *Modelo de Vista 4+1*.

### 1.1 Arquitetura de Software
Arquitetura de _Software_ é a organização interna de um projecto - um conjunto de vários componentes de _sofware_ e das suas inter-relações. Todos os princípios que regem o _desgin_ e evolução destes componentes fazem parte deste conceito de arquitectura.

A problemática abordada pela arquitetura de _software_ é a escolha da estrutura de um programa. Esta estrutura - _arquitectural pattern_ - tem que servir às necessidades tanto do _sofware_ como dos _developers_, garantindo eficácia na funcionalidade do programa e, simultaneamente, flexibilidade e eficiência de implementação. Após a implementação, é muito custoso fazer alterações ao nível estrutural do programa, daí a grande importância de escolher um _arquitectural pattern_ adequado.

O _architetural pattern_ aplicado no _Hextris_ é, a nosso ver, o de _multitiered architecture_. Neste, todas as ferramentas de visualização, lógica, e _input_ do utilizador estão separadas em componentes diferentes, o que é o que se verifica no jogo em questão. Porém, neste não é necessária a utilização de uma camada dedicada a armazenamento de dados, devido à natureza do software, um jogo.
Achamos que a aplicação deste padrão é adequada, já que separa os componentes em camadas flexíveis e extensíveis, mesmo dependendo umas das outras.

### 1.2 Modelo de Vista 4+1
O conceito de _"view model 4+1"_ foi introduzido em 1995 por Philippe Kruchten como sendo um modelo de visão para "descrever a arquitetura de sistemas de _software_, baseado no uso de multiplas vistas concorrentes". Cada uma desta vistas permite elucidar uma componente da arquitectura do projecto aos diferentes intervenientes:

* Para os engenheiros e _developers_ existe a *visão de implementação* e a *visão de processo*;
* Para os _end users_, clientes e analistas existe a *visão lógica*;
* Para _lead developers_ e _project managers_ existe a *visão evolutiva*.

Adicionalmente, são utilizados *casos de uso* e cenários possíveis para ilustrar o funcionamento do projecto, sendo assim constituinda a visão "+1" deste modelo.
<!--
This model allows the various Stakeholders to find what they want to know about the software architecture. Systems engineers approach it from the Physical View, then the Process View. End-users, customers, data specialists from the Logical View. Project managers, software configuration staff see it from the Development View.

O modelo de vistas 4+1 permite agregar vários pontos de vista sobre o mesmo software para dar uma perspectiva o mais completa possível sobre o mesmo. Este modelo baseia-se em quatro componentes, mais concretamente: vista lógica, representada pelo diagrama de pacotes do projeto; vista de implementação, representada pelo diagrama de componentes, vista de processo, representada pelo diagrama de atividades, e a vista de deployment, represenada pelo diagrama de deployment.

4+1 is a view model designed by Philippe Kruchten for "describing the architecture of software-intensive systems, based on the use of multiple, concurrent views". The views are used to describe the system from the viewpoint of different stakeholders, such as end-users, developers and project managers. The four views of the model are logical, development, process and physical view. In addition selected use cases or scenarios are used to illustrate the architecture serving as the 'plus one' view. Hence the model contains 4+1 views:[
-->
## 2. Vista 4+1
### 2.1. Vista Lógica (_Logical View_)
A vista lógica consiste na abstração sob a forma de um diagrama da estrutura de organização da componente lógica de um projeto.
Neste tipo de diagramas é dada atenção especial à maneira como as classes de um projecto se organizam e interagem entre si, sendo estas agrupadas em "pacotes" lógicos que representam classes logicamente semelhantes e/ou intrinsicamente relacionadas.
O objectivo deste tipo de diagramas é permitir ao seu observador uma percepção da arquitetura de um projeto e das suas camadas lógicas de uma forma geralmente mais abstrata, onde a componente técnica (por exemplo, hardware, detalhes técnicos do código, etc.) toma um papel secundário.

O projeto que abordamos foi realizado recorrendo à linguagem de programação orientada por objectos Javascript. Esta linguagem não possui em si o conceito tradicional de "classe"; no entanto, por ser também uma linguagem baseada em protótipos, é possível simular o comportamento deste tipo de objectos recorrendo a polimorfismos e/ou derivações dos vários objectos criados. Consideramos que foi recorrendo a esta técnica que foi construída a lógica do Hextris. Uma possível corroboração desta asserção é o facto terem sido capitalizadas nos ficheiros do código do projeto a primeira letra dos nomes relativos a objectos do jogo, protocolo geralmente usado em classes.

![Diagrama de componentes](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/logicalviewdiagram.PNG)

Pela análise ao diagrama de vista lógica, inferem-se os seguintes pacotes:

Inicialização, onde são preparadas as componentes necessárias ao início do jogo, tais como elementos visuais, escalas e tamanhos das telas, handlers de input, etc.;

Lógica do Jogo, onde é implementada toda a lógica, mecânicas e funcionamento do jogo, assim como a atualização do seu estado;

Objectos InGame, onde são definidos todos os objectos utilizados no jogo, assim como as suas propriedades (são aqui utilizadas as técnicas de simulação de classes);

Visualização, onde é implementada a visuaização e o render dos objectos e menus do jogo;

Utilizador, onde é gerido e manuseado o input do utilizador;

Utilidades, onde são guardados certos métodos úteis para o resto do código, neste caso, métodos matemáticos ligados à rotação de objectos no jogo.

### 2.2. Vista de Implementação (_Implementation / Development View_)
A vista de implementação tem como objetivo relacionar cada componente do software entre si, e ilustrar as dependências entre eles, do ponto de vista do programador. Também pode ser chamada vista de desenvolvimento.
Normalmente é usado o diagrama UML de componentes para mostrar diretamente esta vista. No diagrama que se segue é possível ver o diagrama de componentes que desenvolvemos relativamente ao software em causa.

![Diagrama de componentes](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/implementationview.jpg)

Cada componente representa uma parte modular do programa. No _Hextris_, o utilizador acede ao jogo através de menus, e portanto todo o input do jogador passa primeiro por estes. Por sua vez, estes menus necessitam das funcionalidades do jogo para o controlar, dependendo portanto do componente Game Engine. Para além disso, estes dois componentes necessitam de desenhar no ecrã todo o ambiente de jogo (dentro e fora dos menus), dependendo portanto das funcionalidades disponibilizadas por Render. Por fim, este último componente depende de bibliotecas de JQuery e outros, definidas em Vendor.

### 2.3. Vista de Processo (_Process View_)
Um diagrama de atividades facilita a compreensão do fluxo entre as várias atividades envolvidas numa aplicação. No diagrama seguinte, é possível ver o fluxo de atividades para o jogo Hextris.
![Diagrama de atividades](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/activitydiagram.PNG)
No início do jogo, é possível observar que a primeira atividade realizada é a inicialização de definições da janela. Isto envolve a definição da resolução do elemento canvas em HTML, da framerate que o jogo terá, adaptação para telemóvel, cores de alguns elementos, entre outras definições.
De seguida, são inicializadas as definições do menu, em conjunto com vários objetos que são responsáveis por receber Input do utilizador(Key listeners), imprimir a imagem(Render) e atualizar o estado atual(Update game).
A partir do menu, podem ser realizadas 3 tarefas: abrir Highscores, que mostrará as melhores pontuações e retornará de seguida ao Menu, Instruções de como jogar, que também retornará posteriormente ao Menu, e Jogar, que levará à inicialização das definições de jogo.
Estas consistem em estabelecer as possíveis cores dos blocos, o número de lados da peça central, velocidade de queda de peças, entre muitas outras. De seguida será iniciado o ciclo de jogo, onde, em conjunto com menu, são usadas as várias funções responsáveis por imprimir a imagem, receber Input e atualizar o jogo.
A saída do processo pode ser alcançada através do menu ou através do jogo ao fechar a janela, não existindo forma interna de sair do jogo, já que é jogado no browser.

### 2.4. Vista Evolutiva (_Deployment View_)
![Diagrama de componentes](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/hextris_deployment.PNG)

### 2.5. Casos de Utilização (_Use Cases_)
Para melhor ilustrar a arquitetura do software em questão, apresentamos em seguida os dois diagramas de casos de uso, elaborado para o relatório anterior e que complementa o que já foi dito neste relatório.

![Diagrama de casos de uso do menu](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/usercasemainmenu.PNG)

No menu principal, o utilizador pode navegar para qualquer uma das seguintes iterações: Play (dá início ao jogo, entrando no estado de jogo), Help (permite visualizar um sucinto resumo que explica as regras do jogo e como jogá-lo, fornecendo ainda links para as páginas pessoais dos seus criadores, para o website do jogo e para as páginas iOS e Android do jogo), Facebook/Twitter (permite partilhar um link para o jogo nas redes sociais Facebook e/ou Twitter) e Get On Google Play/Download On The App Store (remete o utilizador para as já mencionadas páginas iOS e Android do jogo, onde é possível descarregá-lo de graça).

![Diagrama de casos de uso do user](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/usercasediagramgame.PNG)

No estado de jogo, o são disponibilizados aos utilizador as ações de rotação do hexágono (para a direita ou para a esquerda) e a de parar o jogo (símbolo "pause" no canto inferior direito).

Após a terminação do jogo, é incializado o estado de fim de jogo, onde são apresentadas ao utilizador a opção Replay (inicializa um novo estado de jogo) ou Share My Score (dirige o utilizador para o Twitter, sugerindo-lhe um post no qual são apresentados a sua pontuação e um link para o jogo). O utilizador pode ainda, neste estado, partilhar o jogo no Facebook ou Twitter.

### Relatório elaborado por:
* [Gonçalo Ribeiro](https://github.com/gribeirofeup),  goncalo.ribeiro@fe.up.pt - 25%
* [Nuno Corte-Real](https://github.com/nunocr), 	up201405158@fe.up.pt - 25%
* [Nuno Martins](https://github.com/Spininador), 	up201405079@fe.up.pt - 25%
* [Rui Soares](https://github.com/RuiCS),		up201404965@fe.up.pt - 25%

<!-- The goal of this third assignment is to document the architecture an design choices of the software application of choice. 

In particular, this report should discuss the following

Introduction to Software Architecture and the 4+1 Architectural View Model; What are the architectural patterns followed by your project (if it doesn't follow any well known one, discuss whether it would be best to do so).
Grade: 4pts
Logical View
Grade: 4pts
Development View
Grade: 4pts
Deployment View
Grade: 4 pts
Process View
Grade: 4 pts
Submission date (i.e., last commit to the repository): 23:59, 20-11-2016.

Note: Include contribution of the team members in the report. It also has to be clear from the commits to the repository the contributions of the different team members. 
-->
