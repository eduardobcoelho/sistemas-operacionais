# Aula 03 - Chamada de Sistema e Interrupção

## Chamadas de Sistemas

* Se uma aplicação precisa realizar alguma instrução privilegiada (**imprimir um arquivo**), ela realiza uma **chamada de sistema**, que altera do **modo usuário** para o **modo kernel**;
    * Exemplo: ler um arquivo.
* Chamadas de sistemas são a porta de entrada para o **modo kernel**;

#### Como elas são realizadas?

1. As chamadas de sistemas são realizadas através de intruções **Traps**.
2. Traps são conhecidos como **interrupções de software**
3. Após o término da chamada (ex.: ler um arquivo), a execução **continua após a chamada de sistema**.
4. Faz a chamada pro sistema operacional --> o SO passa a requisição pro nível de hardware.
5. Manuseia, identifica que chamada que ocorreu e executa o procedimento para voltar a executar o sistema.

#### Passos p/ Chamada de Sistema

1. Aplicativo faz chamada ao sistema (Trap)
2. Através de uma tabela, o SO determina o endereço da rotina.
3. Rotina de serviço é acionada (**rotina compartilhada**).
4. Serviço solicitado é executado e o controle retorna ao aplicativo.

#### Interfaces das SysCalls

1. Interface para esconder a complexidade das *syscalls*.
2. Interface de programação fornecida pelo SO.
3. Geralmente escrita em linguagem de alto nível (C, C++ ou Java).
4. Normalmente as aplicações utilizam uma **Aplication Program Interface(API)**.
5. Interface que encapsula o acesso direto às chamadas ao sistema.

* Motivos para utilizar APIs em vez de chamadas de sistema diretamente:
    1. Portabilidade - Independência da plataforma
    2. Esconder complexidade inerente às chamadas ao sistema
    3. Acréscimo de funcionalidades que otimizam o desempenho

* Exemplo de uso com printf()
    * Programa em C que invoca a função de biblioteca **printf()**, que por sua vez chama o system call **write()**
    * A chamada **printf()** ocasiona a chamada **write()** e **exit()**

## Interrupções

* Vimos que um software pode interromper seu próprio processo (ao fazer uma chamada ao sistema):
    1. Usando **traps** (interrupções de software ou execeções).
    2. Para isso, a aplicação tem que estar rodando.
    * Mas ocorrem **interrupções que não são causadas por aplicações em execução**:
        1. Interrupções de hardware (**eventos externos**)
        2. Um sinal elétrico no hardware.
        3. Causa: dispositivos de E/S ou o clock.
* O tratamento de uma interrupção é o mesmo de um **trap**.

## Interrupção vs Traps

#### Interrupção

* **Evento externo ao processador**
* **Gerada por dispositivos** que precisam da atenção do SO. Pode não estar relacionada ao processo que está rodando.

## Traps

* Evento inesperado **vindo de dentro do processor. Causados pelo processo corrente** no processador (seja por chamada ao SO, seja por instrução legal).