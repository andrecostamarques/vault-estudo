# Recapitulando:
Vimos até agora sobre [[Aprendizado Supervisionado]]. Lembrando, um tipo de treinamento de máquina que tem como característica dados já caracterizados e funcionando de maneira preditiva.
# Planejamento:
Agora, vamos entrar no mundo do [[Capitulo 3 - Aprendizado Não-Supervisionado]], o objetivo desse estudo é analisar e entender os algoritmos por trás dos conceitos de Machine Learning para a categorização de dados em grupos e clusters. Para primeiro compreender e entender o conteúdo do material, devemos compreender os conceitos de pré-tratamento dos dados e das técnicas de Componentes Principais.
# Conteúdo:
Afinal, o que é Aprendizado Não Supervisionado?
É uma família de algoritmos que só receberá variáveis independentes, não terá uma resposta esperada Y, em outras palavras, **a informação não pode ser categorizada.**

E como verificamos o resultado desse aprendizado?
Não existe uma maneira categórica de avaliar o resultado, afinal, não temos uma variável dependente, **a maneira que usamos para validar o método é relacionada com a formação de grupos retornada!**

## Componentes Principais
Uma das técnicas de ANS (Aprendizado Não Supervisionado) é a utilização de Componentes Principais. Seu objetivo é substituir um grande número de variáveis por um componente menor, facilitando a visualização e a extração de features importantes para o treinamento.

Afinal, é mais fácil visualizar 2-3 variáveis que 20 ou 30 que apresentam inter-relações complicadas. É importante perceber como essa técnica é util para o ANS, pois aqui, diferente do AS, as relações entre as variáveis não é de extrema necessidade, afinal, iremos somente agrupar e entender as relações e não necessariamente prever uma variável Y.

A técnica de ACP transforma um conjunto de variáveis **correlacionadas entre-si** em um conjunto de variáveis **Não Correlacionadas**, vamos entender:
- Sabemos que quanto mais as variáveis são correlacionadas com o modelo, melhor, afinal, temos uma predição melhor do caso. Porém, sabemos isso de AS, em ANS é diferente, não temos a necessidade de predição.
- Aqui temos outro problema, queremos categorizar e agrupar as variáveis, isso pode ser dificultado se tiverem variáveis que representem a mesma informação, por exemplo:
	  m² ou pé² - Ambas representam área, podemos agrupa las sem perder potência do modelo.
- Dessa forma, queremos diminuir a quantidade de variáveis que são relacionadas entre si, queremos utilizar então componentes que representem essas variáveis.

**É importante situar que: A técnica de Componentes Principais pode ser utilizada para [[Aprendizado Supervisionado]], porém é utilizada como uma técnica de Pré-Processamento de dados, ao invés de um algoritmo inteiro.**

### Como fazer esse agrupamento?
A Análise de Componentes Principais, para isso, faz uma combinação linear das variáveis.

Vamos supor que temos as variáveis: 
X = $[X_{1},X_{2},\dots X_{n}]$
Teremos então as componentes: 
Y = $[Y_{1}, Y_{2}, . . .Y_{m}]$

Onde: $Y_{1} = a_{11}X_{1} + a_{12}X_{2} . . . a_{1m}X_{m}$
Cada componente é uma soma dos X e da matriz de $a_{ij}$, pesos.

Os Componentes são obtidos em ordem decrescente de importância, então, Y1 explica o máximo possível da variância, Y2 um pouco menos, etc.

A somatória de todos os $Y_s$ resulta na variância total de X, dessa forma, podemos utilizar somente os primeiros, sem perda de informação.
#### Quando usamos Análise de Componentes Principais?
Devemos usar quando tivermos muitas variáveis independentes, mesmo para o AS. 
Quando tivermos [[Métricas Importantes#Multicolinearidade|Multicolinearidade]] -> Isso é: 2+ variáveis representarem a mesma informação!

## Como obtemos os Componentes?
Para isso, será necessário relembrar os conceitos de autovetores e autovalores.
Cheque aqui: [[Métricas Importantes#Autovalores e Autovetores|AutoValores e AutoVetores]].
### Teorema da Decomposição Espectral:
Nos diz que você pode quebrar uma matriz simétrica A com parte mais simples que revelem sua estrutura, envolve autovalores e autovetores.

Qualquer transformação pode ser representada como um "esticar ou encolher" o espaço perpendicular entre si.

É necessário que a matriz seja simétrica, ou seja, $A = A^t$
Para uma matriz A simétrica, há uma matriz de autovalores, tal qual que:

**$\Lambda$ | Matriz de Autovalores** = Matriz diagonal, onde todos os elementos da diagonal são autovalores de A.
	Lembrando: Autovalores são os $\lambda$, eles vão multiplicar a matriz de autovetores, resultando em uma matriz A, transformada pelos autovalores $\lambda$.

![[Pasted image 20250602190709.png]]

Ou seja, são listas de maneira decrescente, onde cada um dos autovalores representa um fator de esticamento  ou encolhimento do autovetor.

**P | Matriz de Autovetores** = [[Métricas Importantes#Matriz Ortogonal|Matriz Ortogonal]] (N x N), cada coluna de P é um autovetor correspondente ao $\lambda$ da Matriz de Autovalores.

Permitindo uma lista de equações que nos permitem realizar transformações com as 3 matrizes:
![[Pasted image 20250601155653.png]]

### Próxima etapa:
Já entendemos que a ACP quer criar novos componentes ($Y_{1}, Y_{2}, \dots, Y_{3}$), e que $Y_1$ deve explicar o máximo das variâncias.

O primeiro Componente da observação é a combinação linear:
$$Y_{1} = a_{11}X_{1} + a_{12}X_{2} . . . a_{1m}X_{m}0$$
$$\therefore$$
$$Y_{1} = a_{1}^tX$$
Podemos escrever desse jeito também, ou seja, multiplicando o vetor das variáveis (X) pelo vetor de pesos (a) resultando no componente $Y_{1}$

Queremos então **Maximizar a variância de Y1**, ou seja, queremos que $Y_1$ capture a maior quantidade de variação dos dados originais.

A variação amostral é determinada como: $a_{1}^TSa_{1}$.
	S: [[Métricas Importantes#Matriz de Covariância (S ou $ Sigma$)|Matriz de Covariância]] das variáveis X, ela é simétrica, já estamos tendo um spoiler de onde isso vai.
	a é o **vetor dos pesos**, esse vetor deve ser unitário (ou seja, deve totalizar sua $\sqrt{ }$ em 1) <- É ele que queremos encontrar.
	A Var($Y_1$) é dada pela multiplicação dos pesos, pela Matriz de Covariância e então multiplicada pelos pesos novamente.

A variação vai nos permitir ver o quanto aquele Componente Principal justifica a variação.

Para isso, devemos querer encontrar o vetor a que melhor maximize a variância de Y!

Dessa forma podemos pensar como: **a é um autovetor de S, associado ao seu maior autovalor!**

#### Calculo da maior variação usando autovetores e autovalores!
A solução é $a_1$ é autovetor de S associado ao seu maior autovalor!
Ou seja:
O vetor de pesos, a, é o autovetor da matriz de covariância S, que está associada ao maior autovalor de S.

Ou seja, a variância máximo que Y consegue é exatamente o maior autovalor, se $\lambda_1$ é o maior autovalor, então, Var($Y_1$) é $\lambda_1$.

**Vamos quebrar para entender melhor**

Temos o **vetor a** -> Vetor de pesos, ele que queremos descobrir, ele é o autovetor.
Temos o **vetor X** -> Variáveis, estamos multiplicando pelo vetor a.
Temos a **matriz S** -> Matriz de Covariância.
Temos o **vetor Y** -> Vetor com os novos componentes -> A somatória de $a^TX$.
Temos o **Var(Y)** -> Variância de Y, o quanto ele justifica o modelo.

Queremos achar o vetor a, que maximize a Variância de Y.

a agora é um autovetor, então ele tem um autovalor correspondente $\lambda$.
Vamos usar a Matriz de Covariância para descobrir o valor a.
Então: Sa = $\lambda$a. 
Var(Y) = $a_{k}^tSa_{k} = a_{k}^t(\lambda_{k}a_{k})$ -> Substituímos $\lambda_k$ para podermos calcular a maior Var(Y)

Sabemos que a é um vetor unitário, então Var(Y) = $\lambda_k$.

Dessa forma, agora sabemos que para maximizar Var(Y), devemos encontrar o maior autovalor ($\lambda$) da Matriz S.
Para encontrarmos Var($Y_{2}$), devemos encontrar o **segundo maior autovalor ($\lambda$).**

#### Mas como descobrimos a matriz de autovalores?
Lembra do Teorema da Decomposição Espectral? Ele nos diz que para uma matriz S, ela pode ser decomposta como S = P$\Lambda$$P^T$.
Onde P é a matriz que as colunas são nossos vetores a.

Para isso, realizamos a equação característica: det(S - $\lambda$I) = 0.
Isso é realizado por máquina, usando Python, sendo um calculo difícil para humanos.

Então ele nos retorna a matriz de autovalores, retornando todos os $\lambda$.
Dessa forma temos o calculo de v, $\lambda$, podendo descobrir todos os Componentes que acharmos bons!

## Entendendo a Variância desses Componentes:
OS autovalores ($\lambda$) representam justamente a variância do n-ésimo CP. 
Então, a variância amostral total dos CPs é igual a somatória de todos os $\lambda_i$, ou $S²_1 + S²_2 + . . . + S²_n$.

# O que veremos em frente?
Agora já entendemos como funciona a Análise de Componentes Principais, como funciona o algoritmo de seleção e para que usamos!

Agora, vamos estudar a matemática por trás desse conteúdo!