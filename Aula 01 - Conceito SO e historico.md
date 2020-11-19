# Aula 01 - Conceito de SO e Histórico

## Sistema Computacional

#### Um sistema Computacional cosiste de:

* Um ou mais processadores
* Memória principal
* Discos, impressoras, teclado, monitor, interfaces de redes e outros dispositivos de E/S
* OBS: Programas precisam saber lidar com todos esses elementos

## Importância do SO

#### Aplicação sem SO

* O SO tem a funcionalidade de prover um suporte para as aplicações de forma que o sistema operacional possa desempenhar uma interface entre o hardware e o próprio sistema, logo, uma aplicação sem SO não possui nada disso
* Gasto maior de tempo de programação
* Aumento da dificuldade
* O usuário precisa estar preocupado com os detalhes do hardware

#### Aplicação com SO

* Maior racionalidade uma vez que as funcionalidades de aplicação vai ser incorparada na própria camada de aplicação e as particularidades inerentes a cada dispositivo, estará incorpodada no sistema operacional
* Permite que a aplicação seja mais portável entre dispositivos diferentes
* Maior portabilidadde
* Maior dedicação aos problemas de alto nível

#### Máquina Multinível

* O sistema operacional vai prover toda a funcionalidade básica de forma que as aplicações estarão apenas preocupadas com a funcionalidade do sistema em si que ele foi projetado

## Definição de SO

* Um SO é um programa, ou conjunto de programas, inter-relacionados cuja finalidade é agir como:
    1. Intermediário (ou interface) entre o usuário e o hardware
    2. Gerenciador de recursos

#### Objetivos Contraditórios

* Conveniência
* Eficiência
* Facilidade de evolução
* A melhor escolha sempre DEPENDE de alguma coisa...

#### Vantagens do SO

1. Apresentar uma máquina mais flexível;
2. Permitir o uso eficiente e controlado dos componentes de hardware;
3. Permitir o uso compartilhado e protegido dos diversos componentes de hardware e software, por diversos usuários.

#### Interação com o SO

* O usuário pode interagir com o SO através de uma linguagem de comunicação especial, chamada "**linguagem de comando**".
* E pelos programas dos usuário? Invocam os serviços do SO por meio das "chamadas ao sistema operacional".
*  Programa --> Chamada ao SO --> SO --> Retorno para o programa.
* **Chamadas de Sistema (System calls)** --> Elas permitem um controle mais eficiente sobre as operações do sistema. Chamar a funcionalidade.

## Formas de Processamento do SO

#### **Serial** (Monoprogramação)

* Recursos alocados a um único programa -- apenas um programa fica dentro da máquina.

#### **Concorrente** (Multiprogramação)

* Recursos dinamicamente reassociados entre uma coleção do programas em diferentes estágios -- vários programas ficam dentro do sistema.