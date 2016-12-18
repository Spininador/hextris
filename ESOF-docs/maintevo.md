![Logo da FEUP](http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png)

# [_Hextris_](https://github.com/Hextris/hextris) - A fast paced HTML5 game inspired by Tetris!

![Logo do Hextris](https://raw.githubusercontent.com/Spininador/hextris/esof_hextris/favicon.ico)

## 1. Manutenção de software
Tal como sugerido, procedemos à análise do código do software que escolhemos, agora no contexto da sua manutenção. Para tal, acedemos à ferramenta _Better Code Hub_, que analisa o código segundo dez princípios, que de descreveremos de seguida.

#### 1.1. _Write Short Units of Code_
Avalia o tamanho de cada bloco de código. Blocos mais pequenos são mais fáceis de perceber, reutilizar e testar, sendo portanto,  uma melhor prática de escrita de código.

**Resultado**: Não aprovado.

O software apresenta vários blocos com mais de 15, 30, e alguns até 60 linhas de código, tornando o código denso, e difícil de modularizar e perceber.
Temos por exemplo funções como a _initialize_, em _initialize.js_, que seria muito facilmente divisível em blocos mais simples.
No entanto, percebe-se o recurso a algumas funções desta dimensão. Torna-se difícil recorrer à divisão de funções que poderão, de si, ser únicas.

#### 1.2. _Write Simple Units of Code_

Enquanto que o princípio anterior avaliava a complexidade de blocos de código apenas pela sua dimensão, este avalia cada bloco pela sua complexidade de McCabe (já referida no relatório anterior). Esta complexidade aumenta sempre que se introduzem ramos ao progresso da função, ie,  quando se introduz um bloco _if-else_, um ciclo _for_, etc...
Blocos com menor complexidade de McCabe são mais facilmente testáveis, compreensíveis, e modificáveis.

**Resultado**: Não aprovado.

Este resultado pode ser contestado. O projeto inclui JQuery, uma biblioteca para JavaScript **não elaborada** pelos developers do Hextris, e portanto, na nossa opinião, deve ser excluída da análise de resultados.
Como tal, o projeto apresenta funções com McCabe menores ou iguais a 10, o que não é ideal, mas não é crítico.

#### 1.3. _Write Code Once_

Neste princípio é averiguado se há código duplicado, ou seja, blocos idênticos de código, repetidos mais que uma vez. A duplicação é, como o nome indica, redundante, e torna o código redundante também. Para modificar o código com blocos duplicados é necessário proceder à alteração de cada um dos blocos, o que não é ideal e torna a leitura e o teste do software difícil.

**Resultado**: Aprovado.

Excluindo blocos pequenos demais para serem modularizados, o projeto não tem grandes blocos de código duplicado, e portanto passa neste princípio.

#### 1.4. _Keep Unit Interfaces Small_

Avalia o software de acordo com número de parâmetros em cada função. Funções com mais parâmetros são menos simples e mais difíceis de testar.

**Resultado**: Não aprovado.

Excluindo JQuery, o projeto apresenta apenas uma função com número de parâmetros crítico (7!). No entanto, para uma miríade de outras funções com bastantes parâmetros os developers traduzem alguns como "opcionais", o que não é uma boa prática. Para corrigir isto, agruparíamos alguns dos parâmetros em objetos.

#### 1.5. _Separate Concerns in Modules_

Este principio é um pouco mais complexo. Avalia a dependência de módulos do projeto, ou seja, quantas chamadas de funções de blocos diferentes são efetuadas em cada um dos blocos. Blocos com muitas chamadas a funções de outros módulos são mais dependentes deles, e como tal, mais difíceis de alterar. O objetivo é ter cada módulo o mais independente possível.

**Resultado**: Não aprovado.

Como era de esperar, módulos como _main.js_ dependem de muitos outros módulos para serem executados.

#### 1.6. _Couple Architecture Components Loosely_

Este princípio analisa quantos componentes servem apenas de "interface" entre outros componentes. Isto tem como objetivo manter os componentes não dependentes entre si e que se comportem melhor quando isolados. De entre diversas maneiras de minimizar isto, temos padrões de desenho, por exemplo.

**Resultado**: Aprovado.

Como já tínhamos visto quando elaborámos o diagrama de componentes, não se verifica a presença de componentes "interface" e como tal, o princípio foi aprovado.

#### 1.7. _Keep Architecture Components Balanced_

Este princípio tem a ver com a organização do código externamente. Pretende-se que sejam agrupados em módulos de peso mais ou menos equilibrado, ou seja, com tamanho mais ou menos igual, de modo a ser mais fácil localizar (e gerir) código.

**Resultado**: Aprovado.

No projeto em questão, como temos apenas dois componentes, este princípio é um pouco irrelevante. Contudo, obteve uma uniformidade de 0.44, para dois componentes, ou seja, há bom equilíbrio dos módulos de código.

#### 1.8. _Keep Your Codebase Small_

Este princípio avalia a dimensão geral do código. Projetos com dimensão mais reduzida precisam de menor manutenção e, se necessário, menos mudanças. Para tal, deve-se recorrer também ao uso de bibliotecas e implementações externas, em contraste com soluções "caseiras".

**Resultado**: Aprovado.

Como era de esperar para a dimensão do projeto (um jogo simples em JavaScript), o projeto passa neste princípio (2 man-months/2 man-years). 

#### 1.9. _Automate Tests_

Este princípio avalia a qualidade e automatização dos testes. Projetos com melhores testes são mais previsíveis e seguros.

**Resultado**: Não Aprovado.

O projeto em questão foi elaborado em JavaScript e a ferramenta sugerida apenas avalia testes em ambiente de implementação Java ou C#.

No entanto, como não seria aprovado (0 linhas de teste / 1906 linhas de produção). Já referimos este tópico no relatório relativo a testes. Não foram implementados testes e, como tal, todo o funcionamento é testado apenas pela execução do software.

#### 1.10. _Write Clean Code_

Este princípio tem a ver com a legibilidade do código. Pretende-se a eliminação de blocos (de código) comentados, comentário inúteis, constantes mágicas, etc. Isto torna o código desorganizado e ilegível, o que por sua vez é frustrante para quem possa vir a analisar o código, seja para que propósito.

**Resultado**: Aprovado.

Excluindo um ou outro comentário inútil, o projeto está bem legível (dentro deste parâmetro). Como tal, para nós foi simples analisar o projeto e implementar uma _feature_.

<!-- Discuss Software Maintainability using the SIG metrics (plus add the badge to your .md file). Students should contact the recitations professor in order to be added to the ESOF organization to be able to automatically compute the metrics of interest using the service https://bettercodehub.com/. See the pdf with an example of a report of the interesting metrics and a description of what they represent.  -->
## 2. Processo evolutivo
<!-- Report evolution process (change impact analysis and implementation)
Briefly describe how the feature you decided to evolve was identified; why you decide to evolve that particular feature? How did you locate the parts in the source code that needed to be modified; etc.  

Pela análise a vários outros jogos do estilo do Hextris, nos quais o objetivo é, geralmente, obter uma pontuação elevada e manter um jogo durante o maior tempo possível, concluímos que muitos deles possuem um mecanismo análogo ao que decidimos implementar, e inferimos que esse mecanismos de "combo mode" seria não só fácilmente implementado na lógica do Hextris, como traria uma componente estratégica adicional ao jogo, tornando-o mais dinâmico, fast-paced e possivelmente mais cativante a maiores audiências.-->

Decidimos implementar uma _feature_ ao nível da jogabilidade - o modo *adrenalina*. Este modo consiste num estado de jogo atingido com um _combo_ de 9 pontuações. Durante 8 segundos, os seguintes efeitos são aplicados:
* A frequência da geração de peças é duplicada;
* A côr das peças geradas é sempre a mesma;
* A velocidade das peças é duplicada

Estas medidas permitem dinamizar mais o jogo, adicionando uma componente estratégica adicional. O jogador procurará ativamente fazer combos para atingir o modo adrenalina. Isto funcionará como um _"fix"_ ao sistema de _combos_ implementado originalmente, visto que os _combos_ no estado atual do _hextris_ têm pouco impacto na jogabilidade - apenas aplicam um multiplicador à pontuação obtida, não tendo nenhum efeito externo. Para além disso, também servirá para acelerar a fase trivial e lenta no início do jogo, visto que a velocidade da geração de peças aumenta com o _score_.

Devido às pequenas proporções do projeto, foi fácil identificar as partes do código que deveriam ser modificadas.No entanto, foi um processo um pouco trabalhoso, pois existem muitas porções repetidas de código, e, por isso, foi preciso aplicar a mesma solução em várias zonas.

## 3. Link para pull request

https://github.com/Hextris/hextris/pull/173
### Relatório elaborado por:
* [Gonçalo Ribeiro](https://github.com/gribeirofeup),  goncalo.ribeiro@fe.up.pt - 25%
* [Nuno Corte-Real](https://github.com/nunocr), 	up201405158@fe.up.pt - 25%
* [Nuno Martins](https://github.com/Spininador), 	up201405079@fe.up.pt - 25%
* [Rui Soares](https://github.com/RuiCS),		up201404965@fe.up.pt - 25%
