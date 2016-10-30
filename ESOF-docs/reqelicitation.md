![Logo da FEUP](http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png)

# [_Hextris_](https://github.com/Hextris/hextris) - A fast paced HTML5 game inspired by Tetris!

![Logo do Hextris](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/favicon.ico)

## 1. Requisitos de Software

### 1.1. Introdução
Este relatório visa a análise da Gestão de Requisitos empregue no desenvolvivmento do **Hextris**.

Neste contexto, entede-se por requisito de *software* como uma funcionalidade - desenvolvida ou adaptada - que necessita ser implementada para a resolução de um determinado problema que o *software* pretende solucionar.

A Engenharia de Requisitos é um processo que engloba todas as actividades de definição, documentação e manutenção de requisitos.

### 1.2. Âmbito
Hextris é um jogo cuja inspiração surge no contexto de uma competição de programação, e desenvolvida por um grupo de estudantes. Partindo deste contexto em que foi inicialmente concebido, é um projeto de âmbito de emulação da experiência clássica de jogos infinitos, centrados na defesa de uma área simples e que recompensam o utilizador com pontos. Para além disso, o ritmo rápido e recomeço imediato de rondas do jogo permitem que seja também um jogo ideal para dispositivos móveis.

### 1.3. Descrição
A elicitação dos requisitos deste projecto foi, inicialmente, regida pelo formato competitivo de uma *hackaton*: o jogo tería de alcançar um estado funcional e apelativo num curto espaço de tempo. Como tal, a base do _Hextris_ assenta na sua jogabilidade - interface e controlos responsivos e intuitivos que facilitam a iniciantes disfrutarem da experiência de jogo.

Posteriormente, devido à natureza *open source* do projecto, novas *features* e melhorias foram sendo adicionadas/sugeridas por terceiros, através de *issues* e de *pull requests* no GitHub.

## 2. Especificação de Requisitos
Como o tipo de projeto desenvolvido é um jogo, a maior parte dos requisitos considerados são pertinentes a todas as funcionalidades do jogo em si e da interação entre o utilizador (o único ator) e este. Para além destes, era indispensável considerar todos os requisitos que possibilitam o bom funcionamento e manutenção do jogo.

### 2.1. Requisitos Funcionais
É nesta parte que incide a maior parte das funcionalidades do jogo em si. Como tal, foi os requisitos funcionais (iniciais) foram os seguintes:
* Tempo de jogo potencialmente infinito, limitado apenas pela capacidade do utilizador conseguir manter a área de jogo fora do limite;
* Controlo do ambiente de jogo simples, usando setas de direção em teclado ou deslizes no ecrã num dispositivo móvel;
* Cálculo de pontuação (local);
* Recomeço de ronda rápido;
* Navegação por menus (principal, pausa, sobre);
* Reconhecimento fácil de todos os elementos da área de jogo;
* Possibilidade de partilha de pontuação em diversas redes sociais;
* Possibilidade de jogar em diferentes dispositivos: computador, _smartphone_, _tablet_.

### 2.2. Requisitos Não-Funcionais
Nesta parte dos requisitos são descritos todos os que contribuem para a qualidade total do produto final. São, nomeadamente:
* Adoção de política _open source_;
* Manutenção de uma página com toda a informação relevante sobre o _Hextris_;
* Ser _free to play_;
* Desenvolvido usando Javascript e HTML5.

### 2.3. Elicitação de Novos Requisitos
Através da implementação da política _open source_, qualquer utilizador pode submeter _issues_ e _pull requests_ no repositório do projeto. Aí, pode alertar os developers para a presença de bugs ou propor mudanças e melhorias ao jogo, sejam a nível de jogabilidade (por exemplo, propor mudança na alteração da velocidade do jogo), compatibilidade ou até acessibilidade (por exemplo, mudar as cores dos blocos para ajudar daltónicos).
Se o utilizador que propõe uma mudança efetivamente a implementa, pode submeter um pull request que, após avaliação pelos developers, é _merged_ para o _branch_ principal do jogo, passando a ser efetivamente parte do jogo.

## 3. Casos de Uso
Para demonstrar a utilização do jogo e as suas fronteiras de navegação, foram realizados os seguintes Diagramas de Uso (User Case Diagrams). Estes diagramas permitem visualizar as possíveis ações que o utilizador pode efetuar, dentro do estado de jogo e no menu inicial.

![Diagrama de Uso do Menu Principal](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/usercasemainmenu.PNG)

No menu principal, o utilizador pode navegar para qualquer uma das seguintes iterações: Play (dá início ao jogo, entrando no estado de jogo), Help (permite visualizar um sucinto resumo que explica as regras do jogo e como jogá-lo, fornecendo ainda links para as páginas pessoais dos seus criadores, para o website do jogo e para as páginas iOS e Android do jogo), Facebook/Twitter (permite partilhar um link para o jogo nas redes sociais Facebook e/ou Twitter) e Get On Google Play/Download On The App Store (remete o utilizador para as já mencionadas páginas iOS e Android do jogo, onde é possível descarregá-lo de graça).

![Diagrama de Uso do Estado de Jogo](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/usercasediagramgame.PNG)

No estado de jogo, o são disponibilizados aos utilizador as ações de rotação do hexágono (para a direita ou para a esquerda) e a de parar o jogo (símbolo "pause" no canto inferior direito).

Após a terminação do jogo, é incializado o estado de fim de jogo, onde  são apresentadas ao utilizador a opção Replay (inicializa um novo estado de jogo) ou Share My Score (dirige o utilizador para o Twitter, sugerindo-lhe um post no qual são apresentados a sua pontuação e um link para o jogo). O utilizador pode ainda, neste estado, partilhar o jogo no Facebook ou Twitter.

## 4. *Domain Model*
A utilização de um *Domain Model* é muito útil para compreender o funcionamento do jogo, assim como a interação entre este e o utilizador, de forma a facilitar o desenvolvimento do projeto.

Neste tipo de diagramas é possível observar a interação entre classes que representam conceitos com significado no contexto do projeto, mas que não são classes de software necessariamente, proporcionando assim uma base à construção do produto de uma forma simples e compreensível.

![Domain Model do jogo](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/ESOF-docs/resources/domain-model-game.PNG)

Neste *Domain Model* é possivel observar a interação entre os vários elementos do jogo.
A única função que o User pode realizar é rodar a Hex(Hexagono no centro do jogo), e esta Hex tem 6 Sides(lados) onde vão cair blocos aleatoriamente.
Cada bloco possui uma certa cor, uma velocidade de queda e um ângulo de queda(6 ângulos do total, pois só há 6 Sides).O atributo Docked indica se o bloco já aterrou em cima de outro bloco ou no Hex.
Quando 3 ou mais blocos da mesma cor entram em contacto, é gerada uma combinação, cuja pontuação depende do número de blocos consumidos.A pontuação gerada pela combinação será adicionada a Score, que representa a pontuação total do jogador.


### Relatório elaborado por:
* [Gonçalo Ribeiro](https://github.com/gribeirofeup),  goncalo.ribeiro@fe.up.pt - 25%
* [Nuno Corte-Real](https://github.com/nunocr), 	up201405158@fe.up.pt - 25%
* [Nuno Martins](https://github.com/Spininador), 	up201405079@fe.up.pt - 25%
* [Rui Soares](https://github.com/RuiCS),		up201404965@fe.up.pt - 25%
