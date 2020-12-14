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
<img src="LNA-ideal-1.PNG" width="600"> <br />
#### Figura 2 - Esquemático do circuito amplificador LNA com componentes SMD comercial. Fonte: Autores, 2020.
<img src="LNA-real.PNG" width="600"> <br />
##
Os circuitos foram projetados para operar numa frequência fundamental de 2,4 GHz. O transistor FET ATF-21170 utilizado foi importado da própria biblioteca do ADS, que no qual o datasheet com os principais parâmetros pode ser consultado através do Link: https://pdf1.alldatasheet.com/datasheet-pdf/view/64591/HP/ATF-21170.html. Na Figura 1, é apresentado o esquemático do circuito LNA com valores projetados em componentes ideais, uma vez que, será necessário realizar uma análise crítica do funcionamento do circuito através dos resultados da simulação de Parâmetros-S, ganho, resposta em frequência e ruído, com os resultados apresentado por meio do esquemático da Figura 2, com componentes SMD comerciais da fabricante Murata, inseridos na biblioteca do software ADS. Um detalhe importante está em saber que existe uma derivação da fonte de 3V alimentando outra parte do circuito com valor -0,4V, uma vez que, sabemos que só existe uma única fonte de alimentação necessária para o circuito LNA. A seção seguinte apresenta os resultados da simulação de ambos os circuitos implementados.
## TestBench
A primeira parte do TestBench foi realizada utilizando componentes ideais com objetivo de verificar o comportamento do ganho, resposta em frequência, linearidade e ruído. <br />
Na medida em que o sinal de entrada do amplificador aumenta o sinal de saída também aumenta, contudo, devido a não-linearidade do amplificador o ganho sofre uma compressão quando o amplificador se aproxima da região de saturação, como é visto na Figura 3. a). A simulação do ganho do circuito é realizada através dos parâmetros S usando coeficiente de transmissão direta, parâmetro S21. O gráfico b) da Figura 3 mostra o ganho que o circuito fornece com S21 = 14,124 dB. Para verificar o casamento de saída e entrada, é necessário analisar o coeficiente de reflexão da entrada S11 = -2,094 dB e saída S22 = -11,925 dB que está apresentado gráfico c) da Figura 3. O próximo parâmetro a ser analisado do LNA foi a sua figura de ruído. Para tanto, pode-se aproveitar a simulação de parâmetros S, e clicar em NF para obter a figura de ruído NF = 0,626 dB que está apresentada no gráfico d) da Figura 3.
#### Figura 3 - Gráficos retirados do ADS através simulação do amplificador LNA com componentes ideais. a)Ponto de compressão 1 dB; b)Ganho do LNA, parâmetro S21; c)Coeficiente de reflexão de entrada (S11) e saída (S22); d)Figura de ruído do LNA. Fonte: Autores, 2020. Fonte: Autores, 2020.
<img src="GraficosIdeais1.PNG" width="600"> <br />
A análise de linearidade fica por conta do ponto de interceptação de terceira ordem IP3. Nessa simulação é analisado sinal de frequência fundamental junto ao sinal de frequência da terceira harmônica no amplificador, para que se possa observar o comportamento da potência de saída em relação a entrada. Com isso, foi verificado esse comportamento, como é mostrado na Figura 4. Assim, pode-se obter 7 dB para o OIP3, -7 dB para o IIP3 e como resultado para o ganho 14 dB.
#### Figura 4 - Gráfico retirado pelo ADS da linearidade através da simulação do amplificador LNA com componentes ideais. Fonte: Autores, 2020.
<img src="GraficosIdeais2.PNG" width="600" > <br />
A segunda parte do TestBench é feita usando componentes SMD comercial seguindo a mesma linha de raciocínio, ou seja, analisar detalhadamente seu comportamento através dos procedimentos aplicados nos gráficos da primeira parte da simulação. Com isso, o ganho do LNA S21 = 13,671 dB pode ser visto no gráfico b), o coeficiente de reflexão na entrada S11 = -2,235 dB e saída S22 = -11,722 dB no gráfico c) e a figura de ruído NF = 0,663 dB no gráfico d) da Figura 5.
#### Figura 5 - Gráficos retirados do ADS através simulação do amplificador LNA com componentes SMD comercial. a)Ponto de compressão 1 dB; b)Ganho do LNA, parâmetro S21; c)Coeficiente de reflexão de entrada (S11) e saída (S22); d)Figura de ruído do LNA. Fonte: Autores, 2020.
<img src="GraficosReais1.PNG" width="600" > <br />
A análise de linearidade fica por conta do ponto de interceptação de terceira ordem IP3 para simulação do amplificador LNA com componentes SMD comercial. O comportamento de não linearidade do LNA encontra-se na Figura 6 logo abaixo. A análise alcançou os mesmos valores para OIP3, IIP3 e ganho da primeira parte. 
#### Figura 6 - Gráfico retirado pelo ADS da linearidade através da simulação do amplificador LNA com componentes SMD comercial. Fonte: Autores, 2020.
<img src="GraficosReais2.PNG" width="600" > <br />
Executando uma comparação entre os resultados obtidos nas duas partes pode-se averiguar que o amplificador utilizando componentes SMD comercial apresenta uma degradação nos resultados por consequência da existência de parasitas, uma vez que, na prática é impossível atingir as especificações de componentes ideais. Além disso, é possível perceber que o coeficiente de reflexão da entrada (S11) apresentou um valor próximo de 0 dB, tanto para os componentes ideais como para os comerciais, devido ao descasamento de impedância para a entrada e saída. Assim, o resultado esperado é que o circuito seja inviável, uma vez que transistor será danificado. Na próxima seção será apresentado o casamento de impedância para o circuito do LNA.
## Casamento de impedância
Para o casamento de impedância foi utilizado duas redes L com componetes LC, para entrada e saída. Além do mais, o projeto dessas redes L foi feito com o auxílio da Carta de Smith presente no software ADS e, além disso foi adicionado uma degeneração indutiva na fonte do transistor. Com isso, o circuito com as redes para o casamento de impedância é visto nas Figuras 7 e 8 para os componentes ideais e comerciais, respectivamente.
#### Figura 7 – Esquemático do circuito amplificador LNA para componentes ideais e redes L de casamento. Fonte: Autores, 2020.
<img src="Circuito-Ideal.PNG" width="700" > <br />
#### Figura 8 – Esquemático do circuito amplificador LNA para componentes SMD comercial e redes L de casamento. Fonte: Autores, 2020.
<img src="Circuito-Real.PNG" width="700" > <br />
O passo seguinte foi simular novamente para os componentes ideais e comerciais a compressão de ganho, o ganho através do S21, o coeficiente de reflexão para entrada S11 e para a saída S22 e a figura de ruído. Nas Figuras 9 e 10 são vistos esses resultados através de gráficos para o circuto com componentes ideais. Já nas Figuras 11 e 12 são vistos esses resultados através de gráficos para o circuto com componentes SMD comercial.
#### Figura 9 - Gráficos retirados do ADS através simulação do amplificador LNA com componentes ideais e redes L de casamento de impedância. a)Ponto de compressão 1 dB; b)Ganho do LNA, parâmetro S21; c)Coeficiente de reflexão de entrada (S11) e saída (S22); d)Figura de ruído do LNA. Fonte: Autores, 2020.
<img src="Graficos-Ideal.PNG" width="600" > <br />
Como já dito antes, a análise de linearidade fica por conta do ponto de interceptação de terceira ordem IP3, em que, está análise é mostrada na Figura 10 para o circuito com componentes ideais e Figura 12 para circuito com componentes SMD comercial.
#### Figura 10 - Gráfico gerado a partir do ADS para a linearidade através da simulação do amplificador LNA com componentes ideais e redes L de casamento de impedância. Fonte: Autores, 2020.
<img src="Grafico-Ideal-Lin.PNG" width="600" > <br />
A partir dos gráficos vistos na Figura 9 é possível notar uma melhora significativa para o coeficiente de reflexão de saída e entrada, com valores de S11=-33,626 dB e S22=-14,161 dB. Além disso, o ganho caiu para 10,821 dB, a figura de ruído passou a ser 0,279 dB, o ponto OIP3 assumiu 20 dB e o IIP3 aumentou para 10 dB.
#### Figura 11 - Gráficos retirados do ADS através simulação do amplificador LNA com componentes SMD comercial e redes L de casamento de impedância. a)Ponto de compressão 1 dB; b)Ganho do LNA, parâmetro S21; c)Coeficiente de reflexão de entrada (S11) e saída (S22); d)Figura de ruído do LNA. Fonte: Autores, 2020.
<img src="Graficos-Real.PNG" width="600" > <br />
#### Figura 12 - Gráfico gerado a partir do ADS para a linearidade através da simulação do amplificador LNA com componentes SMD comercial e redes L de casamento de impedância. Fonte: Autores, 2020.
<img src="Grafico-Real-Lin.PNG" width="600" > <br />
Para os gráficos da simulação de componentes comerciais, é notado através da Figura 11 uma alteração no coeficiente de reflexão de saída e entrada, com valores de S11=-10,119 dB e S22=-17,095 dB. Além disso, o ganho caiu ainda mais para 8,772 dB, a figura de ruído aumentou para 0,486 dB, o ponto OIP3 assumiu 29 dB e o IIP3 aumentou para 20 dB. Esse pequeno déficit de rendimento se dá devido os parasitas que fazem parte da estrutura dos componentes SMD comercial.
## Implementação em Linhas de Microfita 
Realizada a rede de adaptação de impedâncias e verificado o seu funcionamento no circuito do LNA através do TestBench, o próximo passo é preparar o circuito para as etapas finais de projeto. Para isso, inicialmente, o esquemático foi substituido por linhas de microfita entre as conexões dos componentes. A substituição por linhas de microfita em projetos que operam em altas frequências, especificamente em circuitos de RF, é uma forma comum de evitar problemas que são inerentes a esses circuitos e que limitam o seu desempenho de funcionamento. As Figuras 13 e 14 apresentam, respectivamente, os esquemáticos com componentes comportamentais e comerciais. 
#### Figura 13 - Esquemático do circuito amplificador LNA em linhas de microfita com componentes ideais. Fonte: Autores, 2020.
<img src="MLIN ideal.PNG" width="800" > <br />
#### Figura 14 - Esquemático do circuito amplificador LNA em linhas de microfita com componentes comerciais. Fonte: Autores, 2020.
<img src="MLIN real.PNG" width="800" > <br />
Em seguida, foram realizadas simulações para verificar o comportamento do circuito após a substituição por linhas de microfita. A Figura 15 apresenta os resultados da simulação para os componentes comportamentais, que no qual, na letra (a) tem-se o resultado de potência de saída em relação a potência de entrada, que caracteriza a compressão de ganho; em (b) é mostrado o comportamento do ganho na frequência fundamental de S21=10,502 dB; em (c) são apresentados os coeficientes de reflexão S11=-10,346 dB e S22=-12,356 dB; e na Figura (d) o parâmetro figura de ruído do circuito, com um valor de nf(2)=0,421 dB. A análise de linearidade é mostrada na Figura 16, com 29 dB para o OIP3, 20 dB para o IIP3 e com isso o resultado o ganho é 9 dB.
#### Figura 15 - Resultados de simulação do amplificador LNA com componentes comportamentais. a)Ponto de compressão 1 dB; b)Ganho do LNA, parâmetro S21; c)Coeficiente de reflexão de entrada (S11) e saída (S22); d)Figura de ruído do LNA. Fonte: Autores, 2020.
<img src="resultados LNA ideal.PNG" width="600" > <br />
#### Figura 16 - Resultado da linearidade do amplificador LNA com componentes comportamentais. Fonte: Autores, 2020.
<img src="IP3 ideal.PNG" width="600" > <br />
A etapa seguinte foi simular o circuito com componentes SMD comerciais. As Figuras 17 e 18 apresentam, respectivamente, os resultados da simulação. Na Figura 17 (a) como já mencionado anteriormente, tem-se a compressão de ganho, relação de potência de saída com a potência de entrada; em (b) apresenta um ganho na frequência fundamental de S21=8,281 dB; em (c) os resultados dos coeficientes de reflexão S11=-6,919 dB e S22=-13,469 dB e em (d) o valor da figura de ruído em nf(2)=0,699 dB. O gráfico da linearidade é mostrado na Figura 18, com 29 dB para o OIP3, 20 dB para o IIP3 e como resultado 9 dB para o ganho.
#### Figura 17 - Resultados de simulação do amplificador LNA com componentes SMD comerciais. a)Ponto de compressão 1 dB; b)Ganho do LNA, parâmetro S21; c)Coeficiente de reflexão de entrada (S11) e saída (S22); d)Figura de ruído do LNA. Fonte: Autores, 2020.
<img src="resultados LNA real.PNG" width="600" > <br />
#### Figura 18 - Resultado da linearidade do amplificador LNA com componentes SMD comerciais. Fonte: Autores, 2020.
<img src="IP3 real.PNG" width="600" > <br />
Após a comparação dos resutados obtidos após ser inserido as linhas de microfitas, percebe-se uma degradação nos resultos do circuito com compenentes SMD comercial em relação ao circuito com componentes ideais, principalmente no coeficiente de reflexão da entrada o S11, que para os componentes ideais apresentou um valor de -10,346 dB, já para os componentes SMD comercial esse valor passou a ser -6,919 dB, o pode acarretar na danificação do transistor. Essa degradação nos resultados se dá devido a presença de parasitas nos componentes SMD comerciais, uma vez que não se pode eliminar esses parasitas, apenas amenizá-los.
## Conclusões
Neste trabalho foi abordado o projeto e simulação de amplificador de baixo ruído (LNA), que no qual, foi elaborado um testbench para a caracterização do LNA utilizando componentes comportamentais e componentes comerciais. O testbench teve como resultado a simulação do ganho e resposta em frequência, linearidade (IIP3) e ruído (NF). Com isso, foi observado que na frequência fundamental de 2,4 GHz o ganho após inserir as linhas de microfitas foi de 10,502 dB para os componentes ideais e 8,281 dB para os componentes SMD comercial, em que, essa diferença é consequência dos parasitas presente na análise real do circuito. Portanto, esse trabalho foi muito importante para o aprofundamento do projeto e simulação do amplificado LNA, visto que todos os objetivos foram alcançados.
## Trabalhos futuros
Como perspectiva de trabalhos futuros propõe-se otimizar o casamento de impedância através das redes LC já existentes no circuito do LNA.
## Referências
ALMEIDA JÚNIOR, Paulo Acés de. PROJETO DE UM AMPLIFICADOR DE BAIXO RUÍDO E DE UM MISTURADOR DE FREQUÊNCIAS PARA UM TRANSCEPTOR ZIGBEE (2.4 GHz). TCC (Graduação) - Curso de Engenharia Eletrônica, Universidade de Brasília, Brasília, 2016. <br />
RAZAVI. RF Microelectronics. 2nd. Ed. 2011
