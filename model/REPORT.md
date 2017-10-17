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

Propõe-se, baseado no que é observado no vídeo, um modelo no software [Uppaal][ref_uppaal] composto de quatro elementos:

1. PlateCar: carro transportador de placas;
2. Vision: sistema de visão computacional;
3. Robot: robô capaz de atuar nas placas;
4. Controler: controlador responsável por administrar a interface entre os demais elementos;

Cada um dos elementos citados será brevemente descrito nas subseções seguintes.

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
