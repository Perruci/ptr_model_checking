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

[ref_video_theme]: https://www.youtube.com/watch?v=OIeRglPlnUU&feature=youtu.be
[ref_kin]: http://kinemetrix.com
[ref_uppaal]: http://www.uppaal.org
