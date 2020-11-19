# Aula 02 - Tipos e Estruturas de SO

## Tipos de SOs

#### Classificação quanto ao **compartilhamento de HW**

1. Sistemas Operacionais **Monoprogramados ou Monotarefa**:
    * Só permitem um programa ativo em um dado período, o qual permanece na RAM até seu fim (Ex: MS-DOS)
2. Sistemas Operacionais **Multiprogramados ou Multitarefa**:
    * Mantém mais de um programa na memória, para permitir o compartilhamento do tempo de CPU e demais recursos (Ex.: UNIX, Windows)

## SOs Monoprogramáveis ou Monotarefa

1. Caracterizam-se por permitir que o processador, a memória e os periféricos permaneçam **exclusivamente dedicados à execução de um único programa**.
2. Recursos são **mal** utilizados, entretanto, são implementados com facilidade
3. Pode-se pensar que o processo estará em um destes **estados**:
    * nova --> (inicia a execução) executando --> (termina a execução) terminada

## SOs Multiprogramáveis ou Multitarefa

1. A ideia é manter **vários programas** em memória ao mesmo tempo.
2. Há várias tarefas simultâneas, em um único processador: **enquanto uma espera, a outra roda**.
3. Demandam mecanismo de **trocas** rápidas de processos.

#### Classificação de SOs multiprogramáveis

1. **Sistemas Batch**
    * Consiste em submeter ao computador um **lote de programas de uma só vez**.
    * Os jobs (script com lote de programas) dos usuários são submetidos em ordem sequencial para a execução.
    * **Não existe interação** entre o usuário e o job durante a execução
2. **Sistemas de Tempo Compartilhado**
3. **Sistemas de Tempo Real**

#### SO Multitarefa Interativo

1. O sistema permite que os usuários **interajam** com suas computações na **forma de diálogo** .
2. Pode ser projetado como sistema monousuário ou multiusuário (usando conceitos de **multiprogramação e time sharing**).

## Estrutura de SOs

* SOs são normalmente grandes e complexas coleções de rotinas de software.
* Projetistas devem dar grande ênfase à sua organização interna e estrutura:
    1. **Monolítica**
    2. **Micronúcleo**
    3. Camadas
    4. Máquina virtual

#### Estrutura Monolítica

* SO é um **único módulo/bloco**
* Consiste de um conjunto de programas que executam sobre o software, **como se fosse um único programa**.
* Os programas de usuário **invocam rotinas do SO**.

#### Estrutura Microkernel

* Busca tornar o **núcleo** do SO o **menor possível**.
* A principal função do núcleo é **gerenciar a comunicação** entre esses processos.
* Núcleo fornece **serviços de alocação de CPU** e de comunicação aos processos (**IPC**).

#### Estrutura de Camadas

* A ideia é criar um SO:
    1. **Modular** - divisão de um programa complexo em módulos de menor complexidade.
    2. **Hierárquico** - a cada nível, os detalhes de operação dos níveis inferiores podem ser ignorados.
    3. As **interfaces** são definidas para **facilitar a interação** entre os módulos hierárquicos.
* As **interfaces** são definidas para **facilitar a interação** entre os módulos hierárquicos.

#### Estrutura de Máquina Virtual

* Essa estrutura cria um nível intermediário entre o hardware e o SO, denominado **Gerência de VM**
* Esse nível cria diversas VMs independentes.
* Cada VM oferece uma cópia virtual do hardware, incluindo modos de acesso, interrupções, dispositivos de E/S, etc.