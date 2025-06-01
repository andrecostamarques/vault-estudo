#### Pontos iniciais de compreensão:
O que fora falado durante o estudo do [[Aprendizado Supervisionado]] fora para a análise de modelos de regressões, suas variáveis e suas estatísticas. 
Aqui, agora, vamos ter uma visão mais prática e direcionada à sua utilização, em específico, a análise de resultados gerados por Python, seu funcionamento e pontos positivos e negativos.

#### Regressão Linear utilizando Software
Para realizarmos a linearização de qualquer modelo, podemos utilizar de Python, juntamente com bibliotecas como Pandas, para o gerenciamento dos dados e scipy para a análise estatística.

	import pandas as pd
	import statsmodel.api as sm

Ao importarmos essas bibliotecas, podemos criar modelos praticamente instantaneamente, gerando um relatório direto de todas as variáveis analisadas.
![[Pasted image 20250520110926.png]]

#### Análise da Regressão Gerada
É necessário pontuar o seguinte:

**O Modelo gerado não é o mais eficiente, isso é de responsabilidade do usuário definir as melhores variáveis**

Dessa forma, devemos analisar o modelo retornado, verificar possibilidades de melhora e assim iterar para criar um modelo mais robusto.
##### Revisão das Métricas do Modelo:
`R²`: Métrica que varia de 0 à 1, sendo 1 um modelo que é 100% justificado pelas suas variáveis, sendo 0, 0% justificado.

`R² Adj:` O R² ajustado leva em consideração a utilização das variáveis, ou seja, diferente do R², que com lixo, não diminui, o R² Adj leva em considerações as variáveis inúteis e retorna um valor diminuído.

`F-Stats:` É o $F_{calc}$ daquele modelo, devemos comparar com o $F_{crit}$ para a validação daquele modelo. 
	Lembrando que: A validação modelo significa que **ao menos uma variável é significativa**, não que todas são.
	Para calcularmos o $F_{crit}$ usamos a função f.isf();

`Prob (F-statistics):` É a probabilidade da hipótese nula ser verdade, ou seja, ao considerar o $F_{calc}$, qual é a chance de ser falso? 
	Esse valor é análogo ao [[Aprendizado Supervisionado#P_value|p_value]], no sentido de ser uma maneira mais fácil de visualizar a significância.
	< 0.05, significa que a hipótese nula é rejeitada.

##### Revisão das Métricas das variáveis do Modelo:
`coef:`Valor dos parâmetros na equação da regressão

`Std Err:` [[Métricas Importantes#Erro Padrão|Erro Padrão]] das variáveis, o quanto variou ao longo dos dados.

`Teste T-Student:`[[Aprendizado Supervisionado#Estatística T|Teste T]], retorna o $T_{calc}$, igual o $F_{calc}$, devemos comparar com o $T_{crit}$ e verificar se o Teste de Hipótese Nulo é negado.

`P_Value:` É a probabilidade da hipótese nula ser verdade, considerando o valor de $F_{calc}$.
	É uma maneira mais fácil de visualizar a significância daquela variável.
	< 0.05 significa que a Hipótese nula pode ser rejeitada.

`Intervalo de Confiança:` É necessário relembrar que toda análise estatística está sendo realizada em uma amostra, isso significa que todos os valores calculados tem uma margem de erro, o intervalo de confiança. Dessa forma, se existir a mínima possibilidade que aquela variável contenha um 0, é impossível de caracterizar como significativa.
