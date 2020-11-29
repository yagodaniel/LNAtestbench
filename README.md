# LNATESTBENCH
## Tarefa desenvolvida para a disciplina de Circuitos de Radiofrequência, do curso de Engenharia Elétrica, UFERSA, Caraúbas, Brasil.
## Docente: Prof. Dr. Francisco de Assis Brito Filho
## Discentes: Jakson dos Santos Silva, José Ailton de Oliveira Júnior, Yago Daniel Souto
## Resumo
Este repositório apresenta a implementação e o tesbench de um circuito amplificador LNA (Low Noise Amplifier) com o uso do software ADS (Advanced Design System) para sua caracterização utilizando componentes comportamental e SMD comerciais. Resultados de simulação de ganho e resposta em frequência, linearidade (P1dB ou IIP3) e ruído (NF) serão desenvolvidos e comparados.
## Introdução
O LNA é o primeiro estágio presente no receptor após a antena captar o sinal de rádio frequência (RF). Este amplificador apresenta a característica de baixo ruído, em que, sua função é amplificar o sinal recebido de modo a evitar ao máximo que o ruído intrínseco do componente venha a alterar o conteúdo da mensagem captada. Com isso, o LNA deve ser projetado de maneira que apresente uma baixa figura de ruído (NF).
Dessa forma, para se obter uma baixa figura de ruído no LNA, é necessário escolher uma topologia simples para implementação, já que cada componente eletrônico é responsável por introduzir ruído ao sistema. Assim, o LNA pode ser baseado em topologia de um estágio, tais como: porta comum, dreno comum ou fonte comum. A topologia porta comum tem a característica de possuir facilidade em ajustar a impedância de entrada para baixos valores resistivos, de modo, a possibilitar um bom casamento de impedância. Contudo, o ajusto dessa impedância resistiva aumenta a figura de ruído do sistema. Já a topologia dreno comum fornece altos valores para a corrente de saída, no entanto, o maior ganho que pode alcançar é o valor unitário, de modo, a inviabilizar o seu uso no projeto de LNA. Para o amplificador fonte comum, a impedância de entrada pode ser ajustada para baixos valores, com característica capacitiva, além de apresentar um alto ganho de tensão na saída. Além disso, pode-se acrescentar uma degeneração indutiva e, consequentemente na entrada surgi uma componente real, que será útil para o casamento de impedância.
## Implementação da tarefa
Primeiramente, foi realizada a implementação do esquemático através do software Advanced Design System - ADS do amplificador LNA (Low Noise Amplifier) utilizando componentes ideais e SMD comerciais, como mostrado nas Figuras 1 e 2, respectivamente. 
#### Figura 1 – Esquemático do circuito amplificador LNA com componentes ideais. Fonte: Autores, 2020.
![](LNA-ideal-1.PNG)
#### Figura 2 - Esquemático do circuito amplificador LNA com componentes SMD comercial. Fonte: Autores, 2020.
![](LNA-real.PNG)
##
Os circuitos foram projetados para operar numa frequência fundamental de 2,4 GHz. O transistor FET utilizado foi importado da própria biblioteca do ADS. Na Figura 1, é apresentado o esquemático do circuito LNA com valores projetados em componentes ideais, uma vez que, será necessário realizar uma análise crítica do funcionamento do circuito através dos resultados da simulação de Parâmetros-S, ganho, resposta em frequência e ruído, com os resultados apresentado por meio do esquemático da Figura 2, com componentes SMD comerciais da fabricante Murata, inseridos na biblioteca do software ADS. A seção seguinte apresenta os resultados da simulação de ambos os circuitos implementados.
## TestBench
A primeira parte do TestBench foi realizada utilizando componentes ideais com objetivo de verificar o comportamento do ganho, resposta em frequência, linearidade e ruído. <br />
A simulação do ganho do circuito é realizada através dos parâmetros S usando coeficiente de transmissão direta, parâmetro S21. O gráfico b) da Figura 3 mostra o ganho que o circuito fornece com S21 = 14,124 dB. Para verificar o casamento de saída e entrada, é necessário analisar o coeficiente de reflexão da entrada S11 = -2,094 dB e saída S22 = -11,925 dB que está apresentado gráfico c) da Figura 3. O próximo parâmetro a ser analisado do LNA foi a sua figura de ruído. Para tanto, pode-se aproveitar a simulação de parâmetros S, e clicar em NF para obter a figura de ruído NF = 0,626 dB que está apresentada no gráfico d) da Figura 3.
#### Figura 3 - Gráficos retirados do ADS através simulação do amplificador LNA com componentes ideais. a)?; b)Ganho do LNA, parâmetro S21; c)Coeficiente de reflexão de entrada (S11) e saída (S22); d)Figura de ruído do LNA. Fonte: Autores, 2020. Fonte: Autores, 2020.
<img src="GraficosIdeais1.PNG" width="600"> <br />
A análise de linearidade fica por conta do ponto de interceptação de terceira ordem IP3. Nessa simulação é inserida duas frequências na entrada do amplificador, mas que possuem a mesma potência de sinal. Em seguida, foi verificada a potência do sinal de saída mostrada na Figura 4.
#### Figura 4 - Gráfico retirado pelo ADS da linearidade através da simulação do amplificador LNA com componentes ideais. Fonte: Autores, 2020.
<img src="GraficosIdeais2.PNG" width="600" > <br />
A Segunda parte do TestBench é feita usando componentes SMD comercial também para verificar os parâmetros analisados anteriormente. <br />
Esta segunda parte também faz uso dos procedimentos aplicados na primeira parte da simulação dos gráficos. O ganho do LNA S21 = 13,671 dB pode ser visto no gráfico b), o coeficiente de reflexão na entrada S11 = -2,235 dB e saída S22 = -11,722 dB no gráfico c) e a figura de ruído NF = 0,663 dB no gráfico d) da Figura 5.
#### Figura 5 - Gráficos retirados do ADS através simulação do amplificador LNA com componentes SMD comercial. a)?; b)Ganho do LNA, parâmetro S21; c)Coeficiente de reflexão de entrada (S11) e saída (S22); d)Figura de ruído do LNA. Fonte: Autores, 2020.
<img src="GraficosReais1.PNG" width="600" > <br />
A análise de linearidade com ponto de interceptação de terceira ordem IP3 para o simulação do amplificador LNA com componentes SMD comercial é mostrada na Figura 6.
#### Figura 6 - Gráfico retirado pelo ADS da linearidade através da simulação do amplificador LNA com componentes SMD comercial. Fonte: Autores, 2020.
<img src="GraficosReais2.PNG" width="600" > <br />
Executando uma comparação entre os resultados obtidos nas duas partes pode-se averiguar que o amplificador utilizando componentes SMD comercial apresenta uma degradação nos resultados por consequência da existência de parasitas, uma vez que, na prática é impossível atingir as especificações de componentes ideais.
## Conclusões
Neste trabalho foi abordado o projeto e simulação de amplificador de baixo ruído (LNA), que no qual, foi elaborado um testbench para a caracterização do LNA utilizando componente comportamental e componentes comerciais. O testbench teve como resultado a simulação do ganho e resposta em frequência, linearidade (IIP3) e ruído (NF). Com isso, foi observado que na frequência fundamental de 2,4 GHz o ganho foi de x dB, (continuar...). Portanto, esse trabalho foi muito importante para o aprofundamento do projeto e simulação do amplificado LNA, visto que todos os objetivos foram alcançados.
## Referências
RAZAVI. RF Microelectronics. 2nd. Ed. 2011
