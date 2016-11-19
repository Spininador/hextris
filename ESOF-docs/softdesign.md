![Logo da FEUP](http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png)

# [_Hextris_](https://github.com/Hextris/hextris) - A fast paced HTML5 game inspired by Tetris!

![Logo do Hextris](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/favicon.ico)

## 1. Introdução
O presente relatório visa a análise da *Arquitetura de _Software_* empregue no desenvolvimento do *Hetris*. Pretendemos identificar e criticar os diferentes _arquitectural patterns_ que possam estar a ser utilizadoes, assim como analisar este projecto à luz do *Modelo de Vista 4+1*.

### 1.1 Arquitetura de Software
Arquitetura de _Software_ é a organização interna de um projecto - um conjunto de vários componentes de _sofware_ e das suas inter-relações. Todos os princípios que regem o _desgin_ e evolução destes componentes fazem parte deste conceito de arquitectura.

A problemática abordada pela arquitetura de _software_ é a escolha da estrutura de um programa. Esta estrutura - _arquitectural pattern_ - tem que servir às necessidades tanto do _sofware_ como dos _developers_, garantindo eficácia na funcionalidade do programa e, simultaneamente, flexibilidade e eficiência de implementação. Após a implementação, é muito custoso fazer alterações ao nível estrutural do programa, daí a grande importância de escolher um _arquitectural pattern_ adequado.

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

### Relatório elaborado por:
* [Gonçalo Ribeiro](https://github.com/gribeirofeup),  goncalo.ribeiro@fe.up.pt - %
* [Nuno Corte-Real](https://github.com/nunocr), 	up201405158@fe.up.pt - %
* [Nuno Martins](https://github.com/Spininador), 	up201405079@fe.up.pt - %
* [Rui Soares](https://github.com/RuiCS),		up201404965@fe.up.pt - %

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
