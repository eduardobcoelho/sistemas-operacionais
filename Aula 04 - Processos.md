# Aula 04 - Processos

## Definição de Processo

* Um processo é caracterizado por um **programa em execução**.
* Diferença entre processo e programa?
* Um processo é uma instãncia de um programa e possui dados de entrada, dados de saída e um estado (**executando**, **bloqueado**, **pronto**).

#### Programa vs Processo

* Programa
    * Um programa pode ter várias instâncias em execução (em diferentes processos).
    * Algoritmo codificado.
    * Forma como o programador vê a tarefa a ser executada.

* Processo
    * Um processo é único.
    * Código acompanhado de dados e estado.
    * Forma pela qual o SO vê um programa e possibilita sua execução.

#### Processo em Primeiro Plano

* Interage com o usuário.
* Exemplos:
    1. Ler um arquivo.
    2. Iniciar um programa (linha de comando ou um duplo clique no mouse).

#### Processo em Segundo Plano

* Processos com funções específicas que independem de usuários - daemons:
* Ex.:
    1. Recepção e envio de emails.
    2. Serviços de impressão.

#### Cada Processo Possui

1. **Conjunto de instruções**
2. **Espaço de endereçamento** (espaço reservado para que o processo possa ler e escrever - 0 até max)
3. **Contexto de hardware** (valores nos registradores, como PC, ponteiro de pilha, e reg.de prop. gerais)
4.  **Contexto de software** (atributos em geral, como lista de arquivos abertos, variáveis, etc.)

#### Espaço de endereçamento

1. **Texto**: código executável dos(s) programa(s);
2. **Dados**: as variáveis;
3. **Pilhas de Execução**:
    1. Controla a execução do processo;
    2. Empilhando chamadas a procedimentos, seus parâmetros e variáveis locais, etc.

#### Tabela de Processos

1. Também chamada de **BCP** (Bloco Controle de Processo).
2. Contém informações de contexto de cada processo (ex. **ponteiros de arquivos abertos, posição do próximo byte a ser lido em cada arquivo, etc.)
3. Contém **informações necessárias para trazer o processo de volta**, caso o SO tenha que tirá-lo de execução.
4. Contém **estados de um processo em um determinado tempo**.
5. O BCP **só não guarda o conteúdo do espaço de endereçamento** do processo.
6. Assim, um processo é **constituído do seu espaço de endereçamento e BCP** (com seus registradores, etc.), representando uma entrada na tabela de processos.

#### Características de Processo

1. Processos **CPU-bound** (orientados à CPU): processos que utilizam muito o processador. O tempo de execução é definido pelos ciclos de processador.
2. Processos **I/O-bound** (orientados à E/S): processos que realizam muito E/S. Tempo de execução é definido pela duração das operações de E/S.
* IDEAL: existir um balanceamento entre processos CPU-bound e I/O-bound.

#### Criação de Processos

1. Inicialização do sistema
2. Execução de uma chamada de sistema para criação de processo, realizada por algum processo em execução
3. Requisição de usuário para criar um novo processo (duplo clique do mouse, etc.)
4. Inicialização de um processo em batch (em sistemas mainframes com proc. em batch).

#### Processos criando outros processos

1. No **UNIX** com a função fork()
    * Cria clone do processo Pai: cópias exatas na memória, mas com identificadores diferentes.

2. No **Windows** com CreateProcess
    * Cria processo Filho, já carregando novo programa nele.

#### Finalizando Processos

1. **Término normal** (voluntário):
    * A tarefa a ser executada é finalizada;
    * Ao terminar, o processo executa uma chamada (comunicando ao SO que terminou): exit (UNIX) e ExitProcess (Windows).
2. **Término por erro** (voluntário):
    * O processo sendo executado não pode ser finalizado. Ex: gcc filename.c; o arquivo filename.c não existe.
3. **Término com erro fatal** (involuntário):
    * erro causado por algum erro no programa (bug). Ex: divisão por 0 (zero): Referência à memória inexistente. Execução de uma instrução ilegal.
4. **Término (involuntário) causado por algum outro processo**, via chamada a:
    * kill (UNIX)
    * TerminateProcess (Windows)

#### Estados de Processos

1. **Executando**: realmente usando a CPU naquele momento.
2. **Bloqueado**: incapaz de executar enquanto um evento externo não ocorrer.
3. **Pronto**: em memória, pronto para executar (ou para continuar sua execução), apenas aguardando a disponibilidade do processador.