# Aula 05 - Processos e Escalonamento

## O que é Escalonador?

* É quem faz a troca de Processos.
* **Escalonador é o processo que escolhe qual será o próximo processo a ser executado.**
* Existem diversas técnicas/algoritmos para escalonamento de processos.
* Nível mais baixo do SO.

#### Mudança de Contexto

* Mudança de estados
* A mudança de contexto leva a um overhead de tempo (**tarefa cara**):
    1. É preciso salvar as informações do processo que está **deixando/entrando** na CPU sem seu BCP.
    2. Salvar o conteúdo dos registradores.

#### Componentes Envolvidos

1. **Despachante**(Dispatcher):
    * Armazena e recupera o contexto;
    * Atualiza as informações no BCP;
    * Processo relativamente rápido (0,1ms).
    * Pega os dados do processador e coloca na memória principal e o processo inverso.
    
2. **Escalonador**(Scheduler):
    * Escolhe a próxima tarefa a receber o processador;
    * Parte mais demorada;
    * Faz a fila e a manutenção da mesma.

#### Quando o Escalonador é chamado?

1. Quando um novo processo é **criado**.
2. Quando um **processo cria outro**, qual executar? Pai ou Filho?
3. Um processo **chegou ao fim** e um processo pronto deve ser executado.
4. Quando um processo **é bloqueado** (dependência de E/S), outro deve ser executado.

#### Quando E/S ocorre, o Escalonador deve:

1. Executar o **processo que estava esperando esse evento**;
2. **Continuar executando o processo** que já estava sendo executado;
3. **Executar um terceiro processo** que esteja pronto para ser executado.

#### Categorias do Escalonador

1. Preemptivo:
    * Quando um processo pode, por algum motivo, perder seu uso da CPU.
    * Provoca uma interrupção forçada de um processo para que outro possa usar a CPU.

2. Não Preemptivo:
    * Permite que o processo sendo executado continue executando.
    * Condições de parada do Não Preemptivo:
        1. Termine de executar;
        2. Solicite uma operação de entrada/saída;
        3. Libere explicitamente o processador, voltando à fila de prontos.

#### Algoritmos de Escalonamento

1. Sistemas Batch (Lote)
2. Sistemas Interativos
3. Sistemas de Tempo Real

#### Algoritmos de Escalonamento em Batch

1. First-Come First-Served
    1. Não preemptivo
    2. Processos são executados na CPU seguindo a ordem de requisição;
    3. Fácil de entender e programar;
    4. Primeiro que chega, primeiro a ser escalonado;
    5. Processo só é interrompido por E/S, ou quando é finalizado.
    * OBS: Ineficiente quando há processos que demoram na sua execução.

2. Shortest Job First (Lote)
    1. Não preemptivo;
    2. Deve-se prever o tempo de execução do processo;
    3. Menor processo da lista é executado primeiro;
    4. Menor turnaround (médio).
    * **Desvantagens**:
        1. Todos os jobs precisam ser conhecidos de antemão;
        2. Se jobs curtos começarem a chegar, os longos podem demorar as ser executados.

3. Algoritmo Shortest Remaining Time Next (Lote)
    1. Preemptivo;
    2. Versão preemptiva do Shortest Job First;
    3. Processos com menor tempo de execução são executados primeiro;
    4. Se um processo novo chega e seu tempo de execução é menor do que o do processo corrente na CPU, a CPU suspende o processo corrente e executa o processo que acabou de chegar.
    * **Desvantagens**:
        1. Processos que consomem mais tempo podem demorar muito para serem finalizados se muitos processos pequenos chegarem (**inanição ou starvation**).
        2. Exceto que, pela preempção no Shortest Remaining Time Next, o processo, mesmo rodando, seja interrompido.
        3. No Shortest Job First, se der a sorte de começar a rodar, vai até o fim.