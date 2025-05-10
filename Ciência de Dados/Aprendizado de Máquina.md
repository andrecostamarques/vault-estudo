Métodos de aprendizado:

- Supervisionados
Objetivo: 
Prever Y usando X[]
	Métodos: Redes Neurais, Regressões, Algoritmos.

- Não Supervisionados:
Objetivo: 
Não há Y, só X[] -> Buscar informações e relações entre as variáveis X, geração de agrupamentos, clusters.

### Aprendizado Supervisionado:
#### Modelos de Regressão:
Igual o método dos mínimos quadrados, é descobrir uma reta que caracterize o modelo, todavia, diferentemente do feito em aulas e no notebook, é um modelo multi-variado.

Modelo mais utilizado, provavelmente.
	 Busca entender o comportamento de um determinado fenômeno e o comportamento de uma ou mais variáveis preditoras.
	 É muito importante também que: Não se confunda causa e correlação, algumas vezes, uma variável não demonstra causa, ela é causada, juntamente com o fenômeno de predição, por uma outra terceira.
##### Modelos de Regressão Simples e Múltipla:
- Como se compartam as relações entre um conjunto de variáveis explicativas e uma variável dependente (fenômeno de estudo).
	Pode ser generalizado como
	Y = a1 + b1 * X1 + b2 * x2 + b3 * x3 . . . + u
Y = Fenômeno observado.        b = Pesos de cada variáveis.
Xi = Variáveis explicativas.        u = Erro inerente do tamanho da amostra.
