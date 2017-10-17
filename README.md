# Real Time Processes Model Checking

Proposed model for an industrial robot workspace guided by a 3D computer vision system. This project is an assignment of the class 2017/2 Real Time Processes, Universidade de Brasília.

### Chosen Theme

The model proposed must be inspired by the following video:

* Vision Guided Robots: https://youtu.be/OIeRglPlnUU

### Assignment (portuguese)

* Escreva o modelo UPPAAL do processo relativo ao item. Use o vídeo como referência de especificação, descrição e temporização do seu modelo: (70% da nota)

- Definir os modelos, incluindo os modelos discretos de tempo no seu modelo: 35% da nota

- Especificar e definir as propriedades de interesse, incluindo as propriedades atômicas, verificando, inclusive se o modelo está livre de deadlock. (35% da nota)

Na sua solução, voce tem liberdade para criar um modelo do sistema mostrado no vídeo, mas tome cuidados com esses pontos:

- O modelo deve focar nos aspectos concorrentes do modelo

- Um operador humano pode fazer parte do modelo, com comportamento simplificado se for o caso

- o modelo mais abrangente (incluindo todas as fases do processo) é preferível a um modelo limitado, ainda que aprofundado

- aspectos temporais essenciais no processo devem ser modelados: caso as restrições não sejam óbvias, utilize limites de esperas ou atrasos como forma de temporizar seu modelo.

- SUGESTÃO: Procure começar com um modelo simples, e simule. Somente após conseguir realizar a simulação, incremente seu modelo.

A solução da questão deve ser submetida até dia 16 de outubro, as 12:55, na forma de um arquivo compactado, contendo:

- Um relatório em PDF, descrevendo a especificação utilizada (baseada no vídeo), a descrição detalhada do modelo e das propriedades satisfeitas, telas mostrando a simulação e relatórios fornecidos pela ferramenta. Imagens do vídeo devem ser usadas para descrever o processo e relacionar com a especificação e o modelo fornecido. (15% da nota)

- arquivos do projeto: modelo, propriedades satisfeitas, relatórios e resultados da simulação. (15% da nota)

- um vídeo mostrando a temporização da simulação também pode ser adicionado ao arquivo compactado de solução. (10% extra)

## References

BEHRMANN, Gerd et al. UPPAAL 4.0. In: Quantitative Evaluation of Systems, 2006. QEST 2006. Third International Conference on. IEEE, 2006. p. 125-126. ([website](http://www.uppaal.org))

