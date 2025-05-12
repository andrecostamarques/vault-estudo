Tipos de indices: B-Trees, B+Trees, KD-Trees.
Para a acessibilidade de um item, dentro de um [[DBMS]], é necessário a criação de um sistema de indices.

Indices até 5 colunas são eficientes, mais que isso começa a ser ineficiente, ao ponto que, 10 colunas se torna um scan do BD inteiro.

Cada coluna/informação de um dado, é possível criar um sistema de indices. Esse sistema de índice é uma estrutura de dados como HashMap ou B-Trees que permite retornar o dado de uma maneira muito mais eficiente.

Todavia, essa estrutura de dados tem um custo de armazenamento, é necessário que tenha a análise do custo benefício do retorno, o quão eficiente precisa que o dado seja retornado x qual o tamanho do índice.

O sistema de índice é uma estrutura de dados complexa por cada coluna desejada. Por isso, é possível que a estrutura supere o armazenamento do próprio banco.