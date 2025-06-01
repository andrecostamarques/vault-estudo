### Memória Secundária:
- Disco Rígido, Fita Magnética, SSD.

#### Fita Magnética:
- Hoje, atualmente, por ser muito barata, ela ainda é utilizada para funções de BackUp e transporte de informações.

#### Disco Rígido:
- Ainda muito utilizado hoje em dia, tem vários drivers dentro, com cilindros que rotacionam e salvam a informação.
- Velocidade de transferência lenta. E de busca pior ainda.

#### Dispositivos de memória não volátil:
- Atochar muita memória em pouco espaço.
- Semelhante ao SSDs e o Nvme.
- Um grande array de Memória RAM que não é volátil.
- Menor tempo de busca e latência e maior velocidade de transmissão.
- Menor propensão à falha. 

#### Memória Volátil:
- É usar a DRAM (Memória Dinâmica de Acesso Aleatório) para salvar os dados de maneira não volátil.
- Algoritmos que utilizam a memória RAM como memória Cache. Memória RAM na memória Secundária. E por assim vai.
- Cada processo toma um espaço de RAM.
	- Aumentar a RAM do computador não vai ficar mais rápido, só vai ter mais processos ao mesmo tempo.

#### Data Tiering:
- *Quente*: Dados que aparecem mais vezes. -> SSD e RAM.
- *Morna*: Dados estruturados e acessados com frequência moderada. -> HDD
- *Fria*: Dados raramente acessados, estruturados ou não. -> Disco Óptico +  Fita Magnética.

Sempre que for necessário fazer as transferências de dados, é necessário que o SO utilize syscall para essas mudanças, portanto, é por isso que o SO é de tamanha importância para melhorar a eficiência dos processos. 


[[Não sei exatamente o nome da matéria]]