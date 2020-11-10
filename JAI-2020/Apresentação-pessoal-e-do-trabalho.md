# Slide 1 (Apresentação pessoal e do trabalho)

> Olá meu nome é juliano Leonardo Soares

> Sou do curso de ciência da computação e vou apresentar o meu trabalho sobre Redes neurais profundas e algoritmos hierárquicos de pathfinding para descoberta de caminhos em terrenos com altura e inclinação, feito sob a orientação do professor Luis Alvaro

# Slide 2 (Indice)

> Durante esta apresentação mostrarei uma introdução sobre o que são algoritmos de busca de caminhos

> Explicarei como uma Rede Neural Profunda pode ajudar no aprendizado de funções heurísticas

> E porque considerar alturas em algoritmos de busca de caminhos

> Mostrarei os objetivo, e a metodologia que estou usando no trabalho para alcançar estes objetivos

# Slide 3 (Introdução ao que é algoritmos de pathfinding)

> O que são algoritmos de pathfinding

> Pathfinding é o planejamento, de uma aplicação de computador, para resolver problemas de buscas em grafos com a finalidade encontrar uma rota melhor entre dois pontos, Sendo essa melhor rota determinada no algoritmo por critérios determinados como tempo, distância e etc..

> É uma variante mais prática na resolução de labirintos.

> Basicamente são usados em Jogos digitais, robótica, gps e outros

# Slide 4 (Apresentar o algoritmo A\*)

> Neste trabalho, estou tratando especificamente do algoritmo A star que faz parte deste conjunto de algoritmos.

> O algoritmo A-Star é do tipo “gera-e-testa”, isto é, ele gera uma possível situação e testa se ela é a solução. Se for, retorna-a com sucesso, caso contrário, gera outra até encontrar a solução ou não ter mais possíveis situações, quando então retorna fracasso.

> Ele parece idêntico ao clássico “tentativa-e-erro” usando força bruta. O que difere ambos os algoritmos está na forma como o A-Star seleciona o próximo nó a ser aberto, lhe garantindo encontrar em primeiro lugar a melhor solução, podendo então interromper a busca.

> Para conseguir isso, o algoritmo A-Star trabalha com a ideia de “busca melhor-primeiro” e, para determinar qual deverá ser o próximo melhor passo para efetuar todo o seu percurso, ele baseia-se na distância percorrida até encontrar o tal nó, com a menor distância possível até o nó-destino, obtido por meio de uma função heurística.

> O que garante o sucesso do algoritmo A-Star é justamente essa análise não somente da qualidade do nó para chegar no destino, com o uso de uma função heurística h , mas também da qualidade do caminho percorrido até chegar àquele nó a partir da origem, conhecida aqui como função g. Denominando a soma de ambas de f = g + h.

# Slide 5 (Explicação funções heuristicas)

> As Funções heurísticas são usadas para estimar a distância de uma posição atual do mapa até uma posição de destino, ou seja, essas funções usam uma formula matematica que classifica alternativas em algoritmos de pesquisa em que cada etapa da ramificação com base em informações disponíveis ele decide qual ramificação seguir.

> A qualidade desta estimativa está relacionada como a função que se aproxima da distância real até o destino,

# Slide 6 (Função heuristica tradicional x DNN)

> Existem varias Funções heurísticas mas as mais tradicionais são a distância Euclidiana e a distância de Manhattan por serem mais comumente exploradas, exemplo nas imagens.

> Essas funções tradicionais orientam bem a busca por caminhos em mapas de escala relativamente pequena como em mapas usados em cenários de jogos digitais.

> Porem o meu objetivo é usar redes neurais artificiais que podem ser exploradas por algoritmos de pathfinding como funções heuristicas

# Slide 7 (O que são DNN)

> Mas o que são Redes Neurais ?

> Redes Neurais são técnicas computacionais que apresentam um modelo matemático inspirado na estrutura neural de organismos inteligentes como o cérebro de um mamífero que adquirem conhecimento através da experiência.

> Por exemplo nas imagens, o algoritmo tem uma

> Camada de Entrada que esta em vermelho: onde os padrões são apresentados à rede;

> Camadas Intermediárias ou Escondidas, em amarelo: onde é feita a maior parte do processamento, através das conexões ponderadas; que podem ser consideradas como extratoras de características;

> Camada de Saída em azul: onde o resultado final é concluído e apresentado.

> As Redes Neurais Profundas(DNN) são uma classe de algoritmos de aprendizado de máquina que usa várias camadas o que permite extrair progressivamente recursos de nível superior da entrada bruta da rede neural para níveis inferiores até a obtenção de uma saída desejada ou seja em comparação a redes neurais comuns as Redes Neurais Profundas possuem muitas Camadas Intermediárias ou Escondidas:

# Slide 8 (Uso de DNN no aprendizado de funções heurísticas)

> Mas porque o Uso de DNN no aprendizado de funções heurísticas para orientar a busca de caminhos?

> NO trabalho de (Doebber 2020) que foi desenvolvido no grupo de pesquisa onde o trabalho sendo apresentado esta inserido, e que o trabalho corrente expande a investigacao feita em Doebber. ele aborda problemas de busca de caminhos onde redes Neurais Profundas são usadas pelos algoritmos de pathfinding no qual ele investiga o uso de DNN no aprendizado dessas funções heurísticas para melhor orientar a execução da busca de caminhos

> Ele Propõe uma arquitetura de DNN e detalha como preparar as informações de caminho dos mapas virtuais que são usados para treiná-la, de forma que a função heurística aprenda as características mais importante do mapa

> ele também detalha como explorar uma nova abordagem de pathfinding hierárquica baseada no uso de DNN como funções heurísticas,

> O trabalho obteve dados satisfatorios com o uso de DNN nas buscas de caminhos, porem ele foi usado em apenas mapas simulados de labirintos e não em mapas grandes e com mais realismo, portanto o uso de DNN pode ainda ser explorado em novas modalidades e com novos parametros de busca

> como é o objetivo deste trabalho que implementa um pathfinding que une uma busca que considera alturas com algoritimos de redes neurais em mapas reais

# Slide 9 (O que é Pathfinding Hierárquico)

> o trabalho usa o Pathfinding Hierárquico que uma sucessão de pequnas buscas até gerar o caminho completo, ou seja ir fazendo as buscas em pequenos setores, portanto será necessario dividir mapas de grandes dimensões em diferentes clusters e representar esse clusters em um grafo abstrato. e assim computar os menores caminhos entre os nodos A e B afim de Refinar os caminhos encontrados

> assim podendo reduzir os problemas na hora de considerar características topográficas de mapas grandes.

# Slide 10 (Algoritmos de pathfinding considerando inclinação e altura do terreno)

> Mas porque testar os algoritmos de pathfinding considerando inclinação e altura do terreno?

> Os tradicionais funcionam muito bem para encontrar caminhos em áreas que desconsideram características topográficas dos mapas, porem isto não é muito util para mapas reais.

> Mas a forma mais comum usada nos algoritmos de pathfinding para solucionar esses problemas que envolve desníveis de relevo é com o bloqueio dos nodos onde há dificuldades para passar por eles.

> No grupo de pesquisa onde este trabalho de iniciação científica está inserido, a pesquisa apresentada por (Chagas, 2019) trata de problemas de pathfinding onde informações de altura e inclinação no terreno são consideradas

# Slide 11 (Explica trabalho da Caroline)

> No trabalho de Chagas também desenvolvido neste grupo é usado um algoritmo de pathfinding que trata de altitude e suavização de caminhos, nele é implementado e testado um algoritmo que planeja rotas utilizando uma técnica denominada “campo de visão” essas técnicas utilizadas tratam informações que remetem a restrição de altura, sem utilizar apenas o bloqueio ou não de nodos, durante a busca de caminho e isto permite que novos caminhos sejam consideras e não apenas descartados

> exmplo na imagem em que cada nodo é divido em 4 setores leste oeste norte e sul e inserido um valor para atravessar este caminho considerando a inclinação do terreno

# Slide 12 (Continua explicação)

> O trabalho de Chagas busca o menor e melhor caminho de acordo com critérios de evitar inclinações que prejudiquem a movimentação de agentes virtuais utilizados em sistemas de simulação

> Nele a Busca por caminhos é otimizada, e procura por pequenos desvios nas rotas analisadas que recebem uma suavização Com isso o caminho escolhido descreve rotas que permitem o movimento seguro em regiões de montanha

> Como podemos ver na imagem em que no mapa há dois caminhos um encontrados pelo A* padrão representado por círculos e o outro pelo A* tratando inclinações representdo por quadrados portanto usando algoritmos diferentes pode-se obter novos caminhos que podem ser melhores

# Slide 13 (Pathfinding com altura e inclinação normal)

> Na implementação do pathfinding que considera altura e inclinação segue o mesmo padrão de busca comum um f(n) que é o custo para passar do nodo é igual ao custo para passar o caminho mais uma função de heurística

➔ Onde
◆ w = é o coeficiente de análise de altura e inclinação
◆ O(n) = é uma função que calcula a altura/inclinação do nodo n
◆ d(n) = é Distância Euclidiana ou de Manhattan de (n) até o nodo objetivo
e com isto a inclinação e altura é avalida e considerada, podendo resultar em um caminho mais curto a ser considerado

# Slide 14 (Pathfinding com altura e inclinação usando DNN)

> Neste trabalho o algoritimo a abordagem da altura será usado em conjunto com uma rede neural profunda ou seja o resultado da heuristica ira para dentro de uma DNN com o objetivo de otimizar as buscas e verificar a veracidade do melhor caminho com base em redes neurais

# Slide 15 (Objetivo)

> Portanto o objetivo deste trabalho foi unificar algoritmos de pathfinding que tratam altura e inclinação do terreno com algoritmos hierárquicos de busca de caminhos que usam DNN

> O intuito de usar o DNN é para melhor orientar os algoritmos de pathfinding hierárquicos visando reduzir o custo de pesquisa computacional ao lidar com mapas virtuais de grandes escalas

> A metodologia usada foi
> ◆ Computar e avaliar resultados de pathfinding em mapas de diferentes tipos e dimensões, e
> diferentes características de relevo
> ◆ Explorar algoritmos que tratam características topográficas dos mapas durante a busca de
> caminhos, sem utilizar apenas o bloqueio de nodos

# Slide 16 (Metodologia: Experimentos)

> E fazer uma análise estatística dos resultados quanto a Exploração do uso de pathfinding hierárquico e Comparar se estes resultados: DO A* tradicional com altura e inclinação Quanto ao A* com altura e inclinação usando DNN

> Como exemplos nas imagens com mapas de diferentes tamanhos e percentuais de altura e inclinação como em mapas (101x101) nodos e (202x202) nodos e outros maiores

# Slide 17 (Metodologia: Representação dos Mapas)

> Outra metodologia foi representar os mapas

> utilizando grids regulares como no exemplo
> onde X: são os nodos bloqueados
> e em branco são os possiveis caminhos a serem encontrados
> neste exemplo temos um Mapa pequeno representado como um grid
> de (30x36): totalizando 1080 nodos
> dos quais 30% dos nodos são bloqueados e 420 nodos abertos
> para movimentação
> ○ A representa a Posição inicial
> ○ B representa Posição final
> e a distancia obtida entre A e B são 38 nodos de caminho
> resultante

# Slide 18 (Metodologia: Treinamento das DNN)

Outra metodologia foi calcular as menores distancias entre todos
os abertos e assim gerando um Data set de treinamento

como no exemplo as imagens onde podemos encontrar varios caminhos com distancias diferente

# Slide 19 (Metodologia: Treinamento das DNN)

> Para na hora de treina usarmos estas distancias Ai, Bi para calcular a heuristica e assim adicionar ao pathfinding

> os Desafios futuros serão usar Mapas de (256x256) que gera um Data set de treinamento: de mais de 2bilhoes. distâncias calculadas e com isto o maior desafio será processar toda esta informação gerada

# Slide 20

> E Aqui apresento algumas referencias utilizadas nessa apresentacao obrigado pela atencao e estou aberto a perguntas.

> Mais alguma pergunta? então agradeço e desejo boa sorte para os proximos
