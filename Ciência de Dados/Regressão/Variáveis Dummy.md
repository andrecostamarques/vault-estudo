Pontos Importantes para relembrar: 
- Já entendemos como funcionam as relações entre as variáveis e as métricas que utilizamos para compreender - [[Métricas Importantes]], [[Amostragem]]
- Entendemos também, como fazemos transformações, para que os dados sejam o mais normais possíveis. Precisamos que os dados sejam normais para que possamos criar uma relação mais direta entre as variáveis. [[Transformação de Dados]]
- Após os dados estarem transformados, pudemos gerar um modelo que melhor retrate a lógica dos dados, para isso, usamos o [[Aprendizado Supervisionado]] para criar modelos de regressão linear!
- Depois disso, aplicamos o modelo na prática, aprendemos a criar e analisar os resultados gerados por Python. [[Regressão Linear Múltipla]].
- Tudo isso que nós vimos fora realizado em um ambiente controlado (amostras e dados quantitativos), agora, iremos analisar como esse estudo se comporta no mundo real, com poucas amostras e variáveis qualitativas.

# Variáveis Qualitativas
Variáveis Qualitativas, muitas vezes não conseguem ser levadas em consideração em um modelo de Regressão Linear, mesmo que, muitas vezes, elas sejam importantes para a compreensão do problema como um todo.

Por exemplo: Em um banco de dados sobre `Transporte para o Trabalho`, é necessário considerar o método de transporte: Carro, À Pé, Público, etc.

Dessa forma, é em situações como essas que utilizamos uma funcionalidade chamada de **Variáveis Dummy**

## Variáveis Dummy
Não podemos, simplesmente, determinar valores quantitativos aleatórios para cada uma das variáveis qualitativas, isso iria diminuir a confiabilidade do nosso processo estatístico. 
Dessa forma, utilizaremos variáveis binárias, que assumem valores de 0 ou 1, assim, simplesmente retornando se aquela variável é significativa ou não, para a relação estudada.

Nota-se que, será sempre utilizado **n-1** variáveis Dummys, considerando n como o número de categorias.
Mas porque n-1?

Esse -1 é necessário por que iremos setar um estado como o padrão, então, a ausência de outras categorias retorna àquele padrão! Vamos considerar o exemplo acima, existem 5 métodos de locomoção ao trabalho: 
`Carro, Onibus, Voando, Teleporte e Caminhando`

Nós, arbritáriamente selecionaremos o método `Carro` como padrão. Então vamos criar 4 variáveis Dummys: `Onibus, Voando, Teleporte e Caminhando`

| Onibus | Voando | Teleporte | Caminhando | Método Selecionado: |
| ------ | ------ | --------- | ---------- | ------------------- |
| 1      | 0      | 0         | 0          | Onibus              |
| 0      | 1      | 0         | 0          | Voando              |
| 0      | 0      | 1         | 0          | Teleporte           |
| 0      | 0      | 0         | 1          | Caminhando          |
| 0      | 0      | 0         | 0          | Carro               |
Como possível verificar na tabela acima, a ausência das outras variáveis significa a validação da variável Carro, uma vez que somente uma variável por vez é selecionada!

Utilizando essa forma, poderemos testar suas significâncias! Ao utilizar os métodos demonstrados no capitulo, podemos verificar quais variáveis justificam as variações!

O modelo final é então gerado com um peso direcionado à aquela variável dummy, assim, a variação é justificada pela sua presença ou ausência!
![[Pasted image 20250520204201.png]]

Nesse passo, finalizamos o conteúdo sobre [[Regressão Linear Múltipla]]. Verificamos todo o percurso, desde a análise dos dados, à transformação, criação do modelo e sua aplicação no mundo real! 

Agora iremos abranger o estudo para um tipo de aprendizado não supervisionado, a leitura e análise de padrões entre os dados, sem relação com uma variável dependente! 
