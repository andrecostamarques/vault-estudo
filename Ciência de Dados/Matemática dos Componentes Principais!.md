# Recapitulando:
Vimos até agora sobre [[Aprendizado Supervisionado]]. Lembrando, um tipo de treinamento de máquina que tem como característica dados já caracterizados e funcionando de maneira preditiva.
No último material, vimos também a parte teoria de [[Componentes Principais]], como eles funcionam e para o que.
# Planejamento:
Agora, vamos relembrar rapidamente o que aprendemos sobre Análise de [[Componentes Principais]], vamos ver na prática como podem ser utilizados para [[Capitulo 3 - Aprendizado Não-Supervisionado|Aprendizado Não Supervisionado!]]
# Conteúdo:
## Relembrando:
Vamos lembrar o que fizemos no último material. 
Definimos o porque precisamos de ACP, descobrimos como calculamos isso, e aprendemos os métodos necessários para isso.
Vamos agora pensar nos exemplos práticos, para isso, recomendo seguir além do slide, o vídeo a seguir: https://www.youtube.com/watch?v=3UzV21Ak3uc

## Matemática Prática:
Aqui, vamos demonstrar a prática matemática de como calcular os [[Métricas Importantes#Autovalores e Autovetores|Autovalores e Autovetores]] para o cálculo dos Componentes Principais.

Lembrando o formato de uma [[Métricas Importantes#Matriz de Covariância (S ou $ Sigma$)|Matriz de Covariância]]: 
S = [[Var(X1), Cov(X1,X2)],
	[Cov(X1,X2), Var(x2)]] -> A diagonal principal representa a própria variância daquela informação, ela também é simétrica.

Lembrando a equação padrão: $S.v=\lambda v$
Sendo a Matriz S é nossa Matriz de Covariância.

Lembrando o que vamos fazer: Vamos achar um Autovetor ($v$) que, ao multiplicar a matriz S, será a mesma coisa que ele mesmo multiplicado por uma Matriz de Autovalores ($\lambda$).

Dessa forma, utilizamos a matriz S para descobrir os Autovalores $\lambda$, que usamos para descobrir os valores dos autovetores ($v$), eles sim, usamos para descobrir os PCs!

**Agora vamos à prática!**

Dada a matriz A = {{1,4},{2,3}}

1. O primeiro passo é encontrar os **Autovalores** ($\lambda$)
Para isso, precisamos da [[Métricas Importantes#Matriz Identidade|Matriz Identidade]].

	Ao ter a matriz quadrada, queremos achar os autovalores e os autovetores. Queremos encontrar v e lambda tal que: Quando fazemos Axv temos lambda x v.

Multiplicaremos a Matriz identidade por $\lambda$. -> Teremos uma matriz de diagonal $\lambda$.
$$\lambda * I$$
Para encontrar os Autovalores, vamos utilizar de determinantes, assim, podemos verificar relações entre as Matrizes de uma forma mais prática.
$$det(A-\lambda*I) = 0$$
Ao fazer essa igualdade, estamos calculando os valores de $\lambda$ para a diagonal principal da Matriz A. Lembrando que: A diagonal principal da Matriz de Covariância retorna justamente a variância daquela variável.

Então virtualmente, estamos igualando $\lambda$ com as variâncias das variáveis.
Estamos retirando $\lambda$ da diagonal principal da Matriz de Covariância.

Ao calcular o determinante da equação, retornamos uma equação polinomial de $\lambda$.
Dessa forma, vamos calcular diferentes valores de $\lambda$, um grau para cada coluna da Matriz.

Dessa forma, calculamos os Autovalores! Esses valores de $\lambda$ que preenchem a Matriz de Autovalores, do maior valor de $\lambda$ para o menor.

2. O segundo passo é encontrar os **Autovetores** (v)
Para cada $\lambda$ retornado, devemos calcular um Autovetor respectivo para ele.
Para isso, também usaremos uma equação simples entre matrizes.

$$(A-\lambda*I) * [x,y] = [0,0]$$
O autovetor que queremos encontrar é justamente o valor de x,y que iguala a zero a equação, uma vez que já temos o $\lambda$.

Para cada valor de $\lambda$ vamos substituir na equação e ter os valores de x,y.

Com os autovetores, é necessário somente fazer a multiplicação das Matrizes e temos os valores de PCs!

**Toda essa conta foi para uma Matriz 2x2, porém, para matrizes maiores, a necessidade é somente de extrapolar os passos!**

## Análise das Variâncias encontradas:
Considerando essa tabela:
![[Pasted image 20250603061516.png]]

Fora calculado o CP1 e o CP2 desses dados, afinal, o que cada um representa?

CP1 é uma "mistura" das variáveis Nota1 e Nota2, que se agregam, podendo assim, utilizar de uma só variável, justificar a variância em uma escala muito maior!

Ela aglomera o melhor das duas variáveis, o que facilita para nós compreendermos os dados. Isso é possível justamente porquê os dados tem correlação positiva entre si, então, podemos "juntar" os pontos positivos deles em um só!

É necessários também, visualizarmos em dados, o quão melhor o CP foi em relação às variáveis: 

$$\frac{Var(Y_{1})}{Var_{Total}}=\frac{\lambda}{Var(S)} = 0.89$$
Dessa forma, CP1 justifica 89% da variação das informações. Conseguimos concentrar 89% da razão dos dados em uma variável só! Olha como a análise de componentes principais é importante!

Podemos concluir que, X e Y tem a mesma variância geral, a diferença é o quão focado é essa variância nos dados, em Y, a maior parte fica em poucas variáveis, enquanto em X, essa distribuição pode ser mais uniforme, heterogênea, não sabemos, é impossível prever.

## O que pode ser melhorado?
Percebemos, até aqui, que a Análise de Componentes Principais tem uma proposta muito boa, focalizar a variância em menos variáveis, isso é ótimo para análises.
Porém, esses componentes são estruturados com base na Matriz de Covariância(S), caso essa informação seja discrepante, então so Componentes também serão.

Em casos onde S tem uma grande discrepância (Escalas diferentes), é necessário realizar uma normalização nos dados. É necessário padronizar que cada variável seja obtida pela [[Métricas Importantes#Matriz R|Matriz R]].

Essa transformação faz que todas as variáveis tenham uma variância de 1, fazendo que a Diagonal Principal de S se torne 1s.

E que a relação deixa se ser sobre X e se torna sobre Z.

Todas as relações se mantém igual, as relação de Variância e etc etc.

# O que veremos em frente?
Finalizamos os conteúdos de Componentes Principais agora! Entendemos a lógica, o porquê e a matemática por trás! 

Seguiremos agora seguindo por outro caminho, vamos voltar ao AS e entenderemos aglomeração e clusterização!


**eu só vou ler o novo slide, bem lido, e correr pra fazer os exercícios** 
