c### Critérios para o SO.
- Recuperar e armazenar mais rápido possível
- Uso otimizado da memória.
	- Memória tem que ser liberada, minimizar a reservada e ocupar o mínimo possível.
- Segurança dos dados:
	- Correção dos dados -> Garantir que os dados sejam formatados e recuperados quando necessário.
	- Isolamento dos dados -> Bolha dos dados, não dividir.

#### Para o programador:
- Os dados são as variáveis 
- Variáveis são armazenadas na memória -> Dependendo da linguagem, podemos alocar memória e desalocar.
- Em python, por exemplo, executado no JVM, não ha a necessidade de alocar memória.
##### Desempenho:
- Depende do número de copias de memória.
##### Espaço:
 - Depende do armazenamento dos dados.
 - Uso dos tipos.
 - Depende da liberação da memória. 
 - ETL -> Extract Transform Load. (Uma estratégia que lida com memória.)
	 - Você transforma o arquivo ANTES de armazenar, isso diminui o tamanho do armazenamento.
	 - No DATA LAKE, por exemplo, não ocorre a transformação do dado, por isso é mais pesado.

## Pesquisar depois -> New SQL -> OLAP.
Deixa querys mais rápidas -> A formatação dos dados são feitas de acordo com colunas, isso deixa as querys mais rápidas e mais eficientes.
Formatação pode aumentar o espaço de armazenamento, pode ficar mais custoso, é uma relação de custo x benefício. 

## Pesquisar depois -> Polax (Pandas com otimização de dados).
O Pandas quando da um read_csv, puxa todo o arquivo pra memória principal, caso seja necessário, usar o Polax (Usa a memória com mais eficiente.)

### Objetivo do SO para lidar com memória:
Cada processo terá um mapeamento de memória diferente -> Isso permite o enclausuramento/isolamento de processo.
Cada memória terá um mapeamento de memória física pra virtual.

Memória Física
- Processo 1
|             10           |
|             20           |
|             30           |
|             40           |
|             50           |
- Processo 2 
|             60           |
|             70           |
|             80           |
|              90          |

Caso o processo 1 queira acessar a memória 30, tudo bem, caso o processo 2 queira acessar SUA memória 30, terá problema, o encapsulamento é quebrado. Por isso são mapeados processos com suas memórias virtuais.

Memória Virtual
- Processo 1
|             10           |
|             20           |
|             30           |
|             40           |
|             50           |
- Processo 2 
|             10           |
|             20           |
|             30           |
|             40           |

Os locais da memória ainda são iguais os da tabela de cima, todavia, é utilizado um """"ponteiro"""" diferente para cada um dos locais, permitindo que os processos tenham suas memórias separadas.
A CPU que verifica o novo local de memória para acessar a nova instrução, isso é chamado de mapeamento.

A tradução pode ser uma realocação simples -> Só um OFFSET, endereço físico de inicio + endereço de memória relativo do processo.

Tem outros tipos de realocação que não são só simples, imagino que tenham alguns que usem hashmap.