# Uppaal Model Checking

**Autor: Pedro Henrique Suruagy Perruci (14/0158596)**, aluno de engenharia mecatrônica, UnB.
* Professora: Genaina Nunes Rodrigues
* Disciplina: Processamento em Tempo Real 2017/2, Universidade de Brasília

## Vision Guided Robots

O tema escolhido foi o vision guided robots, referente ao vídeo [3D Vision Robot Guidance: Blank Destacking][ref_video_theme] da empresa [Kinemetrix][ref_kin].
Ao longo do vídeo, percebe-se 3 principais processos:

* Carro carregando as placas préposicionadas;
* Sistema de visão computacional localizando as placas;
* Dispositivos robóticos que retiram as placas do carro;

## Modelagem Proposta

### Objetivo

Pretende-se modelar as interações em rede das diferentes tecnologias envolvidas no processo industrial mostrado no vídeo.
Dessa maneira, pretende-se verificar por meio do model checking se as interações entre os processos foram modelados de forma adequada para um sistema lívre de deadlocks.
Não foi considerada uma prioridade modelar os processos intermediários de interleaving envolvidos nos transition systems.
Sua maioria, foi condensada em um único estado, com um tempo de execução mais longo.

### Trasition Systems

Propõe-se, baseado no que é observado no vídeo, um modelo no software [Uppaal][ref_uppaal] composto de quatro elementos:

1. PlateCar: carro transportador de placas;
2. Vision: sistema de visão computacional;
3. Robot: robô capaz de atuar nas placas;
4. Controler: controlador responsável por administrar a interface entre os demais elementos;

Cada um dos elementos citados será brevemente descrito nas subseções seguintes.

### Variáveis Globais

``` C
const int fullPlates = 5; // número de placas a serem carregados após a transição empty -> loaded
int plates = fullPlates;  // número inicial de placas
```

Por questões de verossimilhança, decidiu-se que apenas apenas o **robô** é capaz de diminuir o número de placas.
Existe, também, uma transição do modelo **PlateCar responsável** por recarregar o número de placas para o valor *numPlates*.

De forma semelhante, o **sistema de visão computacional** utiliza o **número de placas** como **condição de guarda**.
Torna-se, portanto, responsável por adiministrar as influências desta variável no transition system como um todo.

### Channels Utilizados

Foi utilizado um número razoável de canais de forma a garantir a sincronia entre os diversos transition systems.
A adiministração das mudanças de estado por meio de handshake é essencial para um processo modularizado desta maneira.

``` C
// car -> controler
chan car_loaded;
// controler -> car
chan move_out_workspace;
// car <- controler -> vision
broadcast chan move_to_workspace;
// controler <- vision
chan plate_visible, plate_not_visible;
// controler -> robot
chan get_plate;
```

## Descrição dos Modelos

### PlateCar (car)

O modelo plate car consiste em um *trasition system* de três estados. 
O estado **empty** é inicial e denomina o momento em que o carro não contêm placas e deve ser recarregado.
Sua única possível transição é para o estado **loaded** que representa o carro logo após sua recarga.
Em seguida, o carro deve aguardar no estado loaded até que uma mudança seja solicitada pelo canal broadcast *move_to_workspace*.
Então, o carro passa para o estado **work_ready** em que serão realizadas tanto a localização das placas pela visão computacional, como a atuação dos robôs.
O carro espera, por fim, uma mensagem para sair do espaço de trabalho e retorna para o estado **empty** quando suas placas acabam.

Vale notar que número de placas carregado é representado pela constante *fullPlates* = 5.
Não existem condições de guarda referentes ao número de placas pois escolheu-se que o sistema de visão computacional seria o único a realizar esta interface.

[ref_video_theme]: https://www.youtube.com/watch?v=OIeRglPlnUU&feature=youtu.be
[ref_kin]: http://kinemetrix.com
[ref_uppaal]: http://www.uppaal.org
