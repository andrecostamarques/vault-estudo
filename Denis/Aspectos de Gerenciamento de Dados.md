### Critérios para o SO.
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

Tem outros tipos de realocação que não são só simples, imagino que tenham alguns que usem Hash Map.

### Latência de acesso à memória.
Cada acesso à memória tem uma latência implicita. Por exemplo, o desbloqueio de um Mutex/Semáforo implica nessa latência.

IO Bondery = Tempo da demora para acessar a memória principal.
	IO em um Banco de Dados é relacionado ao acesso de memória principal, não sobre IO Inputs.

Memória:
- Em banco de dados é necessário você otimizar o máximo possível o requerimento da memória secundária/primária. 
- O [[DBMS]] vai receber o pedido do Query Optimzer, assim que o pedido for feito, ele vai ter que pedir pro SO acessar por via do kernel, acessar o Hardware e buscar a informação na memória secundária. 
- [[Acessibilidade de dados]]
-  O [[DBMS]] tem protocolos específicos para controlar concorrências que são diferentes do SO, tudo tem que passar pelo SO.


### Acesso à memória para Processos.
Existe a paginação e frames.
Caso um processo precise acessar uma página que não está mapeada ainda.
Existe a trava daquele processo.
Para a CPU avisar para o processo que ele pode acessar já aquela memória que foi paginada existe duas opções:
1. Polling -> O Processo fica checando toda hora se a informação já está pronta.
	1. "Shrek, a gente já chegou? a gente já chegou? e agora? "

2. Interrupção -> Avisa o SO que a informação está disponível para acesso do processo, isso causa a interrupção de outro processo.
	1. Todavia, o escalonador não precisa enviar o processo que quer a memória, o SO só sabe que a interrupção aconteceu.
	LiveLock -> Existe tanta interrupção que a CPU gasta toda o processamento para lidar com as interrupções.


Perguntar:
Livros de Banco de dados (Tipo, infraestrutura, OLAP, SQL):
	Sistemas de Banco de Dados - https://www.amazon.com.br/Sistemas-Banco-Dados-Ramez-Elmasri/dp/8543025001
	

Livro de estatística (Ciência/Análise de dados -> IA):
	Python Data Science Handbook - https://www.amazon.com/Python-Data-Science-Handbook-Essential/dp/1491912057
	Think Stats - https://www.amazon.com/Think-Stats-Exploratory-Data-Analysis/dp/1491907339
	Statistics101 - Harvard - https://stat110.hsites.harvard.edu/
	Probabilidade Moderna - https://www.amazon.com.br/Probabilidade-Curso-Moderno-com-Aplica%C3%A7%C3%B5es-ebook/dp/B01863RJ7Y
	''

Livros de Machine Learning:
	Hands On Machine Learning - https://www.amazon.com/-/pt/dp/1098125975/ref=emc_bcc_2_i
	Machine Learning Probabilistic Perspective - https://www.amazon.com.br/Machine-Learning-Probabilistic-Perspective/dp/0262018020
	Python Machine Learning - https://www.amazon.com/Python-Machine-Learning-scikit-learn-TensorFlow/dp/1789955750
	