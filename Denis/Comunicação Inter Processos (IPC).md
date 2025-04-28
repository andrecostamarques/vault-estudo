Processos são isolados entre sí, já Threads tem suas funcionalidades e resources compartilhados.

Ideia de Chromium: 
- Processos são rodados independentemente, facilitando a organização e são isoladas, ou seja, mais segurança e mais realibility.
- Cada parte do HTML é processado em um processo diferente.
- IPC é a forma que essas organizações são comunicadas.
- Varios processos permitem que cada parte do site rode de maneira independente.

PiHole -> BlackList de AdBlock em um RaspBerryPI

Configurar o roteador pro DNS passar pelo RaspBerry.

Necessidade de IPC:
- Abstração de Processos é a abstração mais importante de Software que existe, sem ela, não seria possível ter comunicação, seria impossível funcionar um S.O, é importante que várias partes estejam executando de maneira ao mesmo tempo.
- Docker e microserviços só existem por causa do IPC.
- Jeito de fazer comunicação inter-processos, tipo usando o grep Hello World.
- Interação é estática e involuntária, não tem nada falando que vai acontecer, tudo é feito pelo programador, por fora do teu código. -> Modelo de comunicação PipeLine -> P1 -> P2 -> P3 -> ... -> Pn.

Interação por arquivos externos:
	Um processo cria um arquivo, enquanto outro processo lê esse arquivo. (Isso não é um protocolo de comunicação, não há nenhuma garantia entre nenhuma das duas partes.) -> Pode ter problemas de sincronização também.

Exemplo de comunicação em rede:
- Um jogo roda em um ou mais processos em sua máquina local.
- A comunicação é feita via rede (Socket)
- Cada informações são enviadas para o Servidor, que gerencia o protocolo, tcp, udp? como vão ser enviadas as informações?

Região de memória compartilhada, tem variáveis globais entre os processos.
Fila de mensagens.


### Região de Memória Compartilhada:
Kernel aloca memória entre os dois processos.
Os dois processos conseguem acessar esse mesmo espaço de memória como se fossem variáveis globais entre os dois processos.
Oferece um risco da segurança e quebra o conceito de processos separados.

### Fila de mensagens entre processos:
Fila (FiFo) é gerenciada pelo Kernel entre os dois processos, ou seja, qualquer comunicação entre os dois processo é necessário entrar no modo de Kernel -> Mais lentidão para o sistema, causa [[Overhead]] no sistema.

### Diferença entre os dois:
O Kernel gerencia o espaço de memória compartilhado, e o Kernel participa durante toda mensagem/comunicação.

### Problema Produtor-Consumidor:
Quando um processo cria algo e outro processo consome algo.
Existem alguns problemas. 
Buffer Ilimitado, não tem limite prático ao tamanho, produtor nunca espera, o consumidor espera se não houver buffer disponǘeil.
Todavia, o buffer nunca é ilimitado, ele sempre vai ter um tamanho fixo, causando problemas de espera do consumidor.

