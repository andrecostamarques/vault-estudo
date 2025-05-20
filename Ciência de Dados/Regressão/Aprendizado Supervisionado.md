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
	Onde, ui = Yi - $\hat{Y}$ ( $\hat{Y}$ é a leitura naquele local da função (Regressão Simples))

##### Métodos de Regressão Linear:
###### Método dos Mínimos Quadrados (OLS)
- Fenômeno = f(variáveis) 
- Quer se descobrir uma função que represente a formatação dos dados.
No caso do estudo do tempo dos alunos: temp = f(distância)
	$\hat{tempo}$ = $\alpha$ + $\beta\text{ }\cdot$ dist + u

Condição de funcionamento: 
1. Somatória de u deve ser zero. Ou seja $\sum^n_{i=1} u_{i} = 0$
	1. Com somente essa condição, é possível encontrar diversas retas, portanto, é necessário outras condições.
2. Somatória de u ao quadrado é a mínima possível. Ou seja $\sum^n_{i=1} u_{i}² = min$
	1. Juntando com essa condição, escolhe se a reta que apresenta a somatória de menor erro possível em relação aos pontos, ou seja, a que melhor descreve a relação dos pontos totais com uma reta.

Para realizar a minimização dos dados, a equação derivada em a e b para igualar a zero. Dessa forma a Equação retorna: 
	$\alpha = \overline{Y} - \beta \cdot \overline{X}$ em que $\overline{Y}$ e $\overline{X}$ representam a média amostral de Y e X.
	 $\beta$ = ![[Pasted image 20250510192133.png]]

Ao utilizar ambas as contas é possível descobrir a linha que percorre, de maneira a diminuir os erros máximos, dos dados analisados.

**É importante que o pesquisador utilize a linha de regressão de maneira a interpolar os dados que querem ser previstos, pois a extrapolação pode retornar um valor irregular ao esperado**

###### Métrica de análise: R²
A **soma total dos quadrados (SQT)** mostra a variação em Y em torno de $\overline{Y}$.
A **soma dos quadrados da regressão (SQR)** oferece a variação de Y considerando as variáveis X utilizadas no modelo.
A **soma dos quadrados dos resíduos (SQU)** apresenta a variação de Y que *NÃO* é explicada pelo modelo.

Portanto: SQT = SQR + SQU
$Y_{i} - \overline{Y} = (\hat{Y_i} - \overline{Y}) + (Y_{i} - \hat{Y_{i}})$

![[Pasted image 20250510194028.png]]

A partir disso, é possível chegar em R², conhecido como:
#### Coeficiente de de ajuste da Regressão Linear (R²)
O R² é chamado de Coeficiente de ajuste da Regressão Linear, pq é a capacidade do modelo explicar o quanto as variáveis justificam as variâncias de Y.

R² = $\frac{SQR}{SQR + SQU}$ = $\frac{SQR}{SQT}$ 

Dessa forma, ela varia de 0 à 1, justificando um valor de 0 à 100% de variância. O R então pode ser também explicado como: inversamente proporcional ao tamanho dos resíduos.

**Importante: O R² NÃO retorna se a a variável explicativa é estatisticamente significante, somente a variação. É equivocado falar que um alto valor de R² significa robustez do modelo, afinal, não é possível afirmar só com isso que as variáveis são causa e não, consequências.**

Para retornar a significância estatística de um modelo, é necessário a realização de testes estatísticos apropriados para isso.
Tais testes serão citados abaixo.
#### Significância de um modelo e seus parâmetros.
Para descobrimos a significância de um modelo, é necessário realizar um Teste F de hipótese. 

As hipóteses para o modelo são:
$H_0$ = $\beta_i = \beta_{i+1} . . . = \beta_{k} = 0$. -> Isso significa: que TODAS as variáveis não justificam o modelo.
$H_{1} =$ existe ao menos um $\beta_{i} \neq$ 0. -> Isso significa que: ao menos uma variável justifica o modelo.

Ou seja, para um modelo ser significativo, ele necessita negar a hipótese nula.

	Lembrando: B é o multiplicador da variável, ou seja, um multiplicador = 0, significa que a variável é inútil para a regressão.
##### Estatística F
A estatística F ($F_{calc}$) é calcula a partir da expressão: 
![[Pasted image 20250510201529.png]]
Em que: 
- k = número de parâmetros, incluindo o intercepto ($\alpha$)
- n = tamanho da amostra.

A representação de (k-1) é o **grau de liberdade da regressão**, é essa a variável que utilizamos nas tabelas que eu não fazia ideia para o que servia.
Enquanto (n-k) representa os **graus de liberdade para os resíduos** 

Utilizando a [[Tabela F]], podemos concluir que $F_{crit}$ = 5,32.
O F calculado acima é chamado de $F_{calc}$, devemos comparar ele com o $F_{crit}$ que recebemos da [[Tabela F]].

Caso o o $F_{calc}$ seja **MAIOR** que o $F_{crit}$, a Hipótese Nula é **NEGADA** para **TODOS** parâmetros zerados.
Logo, pelo menos uma das variáveis é estatisticamente significante para explicar a variação de Y, assim, podemos considerar que nosso modelo é estatisticamente significante.

#### Avaliação dos parâmetros dentro do modelo:
Como dito acima, com a hipótese nula negada (Teste F), temos certeza que: ao menos UM parâmetro é significativo. Isso prova a significância do modelo, porém, podemos deixar nosso modelo melhor, permitindo somente que os parâmetros significativos se mantenham, para isso, devemos avaliar cada parâmetro por si só.

Para isso, usamos a Estatística T, importante pois fornece a significância de cada parâmetro. Cada parâmetro passa por uma hipótese de teste, além da hipótese de teste do intercepto ($\alpha$).
- $H_{0} : \alpha = 0$ -> Onde: alfa é zero, portanto, a hipótese nula é válida.
- $H_{1} : \alpha \neq 0$ -> Onde: alfa precisa ser diferente de zero, portanto, a hipótese nula é invalida.
- $H_0 : \beta_{0} = 0$ -> Onde: O $\beta$ específico daquele parâmetro é zero.
- $H_{1} : B_{0} \neq 0$ -> Onde: O $\beta$ específico daquele parâmetro é diferente de zero. 

Ao realizar os testes de hipótese de cada parâmetro, é possível que o pesquisador verifique a significância de cada parâmetro e permita a criação de um modelo mais robusto e simplificado ao máximo.

##### Estatística T
A realização dos Testes de Hipóteses T é realizado pelas seguintes equações:

$t_{a} = \frac{\alpha}{s.e(\alpha)}$                                                                                       $t_{\beta_{j}} = \frac{\beta_{j}}{s.e(\beta_{j})}$
Onde: s.e corresponde ao [[Métricas Importantes#Erro Padrão|Erro Padrão]] de cada parâmetro.

O resultado de $t_{a}$ e $t_{b_{j}}$ retornam, respectivamente os $f_{calc}$ de cada um deles. Devemos então puxar a [[Tabela T Student]] e calcular, utilizando o **Grau de Liberdade dos Resíduos** (n-k).

Caso o $t_{calc}$ > $t_{crit}$ podemos considerar que a Hipótese Nula é rejeitada, podendo então comprovar que a significância estatística daquela variável.

##### P_value
Utilizando Python e bibliotecas de estatística, a maioria dos testes, como teste F, são retornados os valores do nível de significância direto, chamados de **p_value.**
O p_value é a chance que, com base nos dados atuais, nós vejamos um dado tão extremo ao ponto dele aceita a hipótese nula. Por exemplo, qual é a chance, que, seguindo o padrão dos dados atuais, tenha um dado nele que aceite a hipótese nula. 

Faz sentido achar que, quanto menor seja a chance de aparecer um dado que aceite a hipótese nula, melhor!

Portanto, quanto MENOR seja o p-value, mais forte é a evidência contra a hipótese nula, indicando que há uma chance muito pequena de observarmos os dados sob a hipótese nula. 

Dessa forma, podemos concluir que: um p_value menor que 0.05 (95% de certeza) podemos afirmar que aquela variável **NEGA** a hipótese nula.
##### Intervalo de Confiança:
Como tudo que estamos calculando é com base em amostras, é necessário que nós consideremos que amostras tem erros, e probabilidades de serem diferentes dos dados completos.
A partir disso, é necessário validar as variáveis levando em consideração essas condições. A partir disso, podemos concluir que uma variável tem seu valor com base em uma faixa.
Consideremos que calculamos uma variável como 0.5, ela na verdade, é uma faixa entre 0.3 - 0.7, considerando que ela pode variar, dependendo da amostra que utilizamos.

Podemos afirmar que com 95% de certeza os dados estarão de x à y.
A partir disso, precisamos calcular esses valores, pois, se houver uma mínima chance de nossas variáveis terem o valor de 0, essas variáveis automaticamente serão consideradas **NÃO SIGNIFICATIVAS** para o modelo.

Para isso, calculamos dessa forma, para as variáveis $\beta$ e $\alpha$.
![[Pasted image 20250510221942.png]]

Caso o intervalo de confiança de um parâmetro contenha 0, mesmo que o teste t e o p-valor indiquem significância estatística, não podemos aceitar a variável no modelo, pois o intervalo sugere que ela pode não ter efeito real no fenômeno estudado

#### Resumo:
Um modelo de regressão linear precisa passar por validações para ver sua significância estatística. 

A primeira linha que podemos passar é a métrica do R², o coeficiente de ajuste de regressão linear.
	Ele vai falar o quanto que o fenômeno estudado é justificado pelas variáveis, todavia, só isso não é suficiente para falar que aquela regressão é significante ou não, afinal, só demonstra a relação e não causalidade.

A partir disso, podemos validar a significância geral do modelo, para isso, devemos passar pelo Teste F. 
	Ele vai realizar o teste para comprovar a hipótese nula daquele modelo.
	A hipótese nula é que TODAS as variáveis são inúteis.
	Portanto, se o teste F rejeitar a hipótese nula, só temos a comprovação que ao menos UMA variável é significativa. 

Portanto, precisamos saber quais variáveis são significativas ou não, afinal, variáveis não significativas podem adicionar ruídos e tirar nossa precisão, como é o R² ajustado.
	Para isso, precisamos realizar o Teste T em todas as variáveis. Precisamos negar a hipótese nula de todas as variáveis para que elas sejam significativas, respectivamente.
	Nele, vamos verificar se aquela variável é significativa, se o $t_{calc}$ > $t_{crit}$ podemos rejeitar a hipótese nula daquela variável.
		Usualmente, usamos também o p_value para verificar, ele é uma forma de expressar essa significância de maneira mais direta, oferecendo uma probabilidade associada à estatística t sem a necessidade de calcularmos o t critico.

Após validarmos as variáveis, negando a hipótese nula delas com o statistics t e o p_value. Precisamos validar se as variáveis são validas FORA da amostra, é necessário lembrar que todos os cálculos que estamos fazendo são relacionados à amostra. Então verificamos seus intervalos de confiança.
	O que é isso? O valor de $\beta$ que calculamos é o valor para aquela amostra, é provável que se a amostra for modificada, aquele valor também será, portanto, temos uma faixa de valor que $\beta$ pode estar.
	Caso essa faixa contenha o 0, podemos concluir que, existe uma possibilidade (nem que mínima) que $\beta$ será não significativa, portanto, **não é possível negar a hipótese nula**.

Dessa forma, passamos por todas as validações das variáveis, devemos ver se o modelo é correlacionado com o R², depois, devemos ver se o modelo é significativo com o TesteF, depois, devemos ver se as variáveis são significativas com o testeF e o p_value, após isso, devemos verificar se as variáveis podem ter suas hipóteses nulas negadas com base no intervalo de confiança!

Pipeline de inclusão de $\beta$:
![[Pasted image 20250510224652.png]]