### Variância e desvio-padrão:
- Conjunto de observações denotadas por s²:
- ![[Pasted image 20250505201927.png]]
- x' = média das observações.
- Desvio Padrão é s = $\sqrt{  (s²)}$.
#### O que significa?
Variância: grau de espalhamento dos dados: quanto maior, pior.
Desvio-Padrão: Em média, os dados estão a S da media.

### Covariância Amostral:
Uma medida de associação entre as observações de duas variáveis. 
- Variáveis k e k': 
- ![[Pasted image 20250505202759.png]]
- Ela mostra a média do produtos das diferenças de cada valor em relação à media da variável.
- Ou seja: se x e y aumentarem ou diminuírem JUNTAS, a covariância será positiva, caso contrário, será negativa.
#### Matriz de Covariância (S ou $\Sigma$):
Lembrando o que é Covariância: 
É a relação entre duas variáveis, ou seja, se elas são proporcionais, diretamente, inversamente ou se não há nenhuma relação entre elas.
A matriz de covariância é onde as informações são guardadas. Ou seja, as relações entre todas as variáveis e como elas se correspondem.

Dessa forma, consideramos que uma matriz de covariância é sempre simétrica, ou seja, é triangular.

### Coeficiente de correlação amostral:
Associação linear entre duas variáveis. 
![[Pasted image 20250505203209.png]]
- r deve estar entre -1 e 1;
- r = 0 -> essas duas variáveis não tem correlação entre si.
- r negativo -> Um valor vai crescer enquanto outro diminui.
- r positivo -> ambos valores serão pequenos ou grandes, juntos.


### Erro Padrão
Diferente do imaginado por mim, erro padrão e desvio padrão são coisas diferentes:
O Erro Padrão mede a precisão da média amostral como estimativa da média populacional, ou seja, é o quão perto da média populacional ele está.

Ele é equacionado como:
EP = $\frac{s}{\sqrt{n }}$, ou seja, é o desvio padrão, divido pela raiz da quantidade de amostra.

Quanto maior for a amostra, menor será o erro padrão, ou seja, a média amostral fica mais confiável. Podemos concluir, que quanto maior a amostra, mais será parecida com a média populacional.

### Multicolinearidade:
Quando duas ou mais variáveis representam as mesmas variâncias.
Ou seja, m² e pé², ambas representam área, são multicolineares.

### Autovalores e Autovetores:
Em uma matriz A, quadrada, ou seja, N x N.

Teremos um valor $\lambda$ que seja diferente de 0.
E teremos um vetor v qualquer diferente de 0, também.

Quando a matriz transformar o vetor v, o resultado será o vetor v multiplicado por $\lambda$.

Sendo redigido por: $Av = \lambda v$

Ou seja, v é o autovetor da matriz A. É um vetor que ao ser modificado pela matriz, ele será igual à multiplicação escalar do Autovalor $\lambda$.

### Matriz Ortogonal:
É uma matriz onde sua inversa é igual sua transposta:
Suas colunas são ortonormais, cada coluna é um vetor unitário e todas as colunas são perpendiculares entre si.

### Matriz Identidade:
Uma matriz que é repleta de 0s, e a diagonal principal preenchidas com 1.
Ela representa o 1 no mundo das matrizes.

### Matriz R
A Matriz de Covariância Amostral porém normalizada com a média e o Desvio Padrão, não precisa saber muito mais que isso.

Em que: $$ Z_{i} = \frac {Xi-\overline {Xi}}{\sqrt{ S_{ii} }}$$
**Acrescentar aqui depois**