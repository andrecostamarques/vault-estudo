- Importante para uma melhor compreensão geral dos dados.
	Notação: Y* = f(Y)
	Onde Y é a variável original e f é uma função.

- A ordem dos dados mantém, e todo são transformados do mesmo jeito.
- Dados não lineares podem ser convertidos para lineares, facilitando os estudos das relações.

## Pressupostos da Transformação de Dados:
- É necessário que todas as variáveis sejam transformadas igualmente. 
- É necessário que as variâncias sejam similares entre variáveis comparadas.
- As variâncias devem seguir uma distribuição normal.
	- Ou seja, os dados devem ser ''errados'' de uma maneira equilibrada.
	- Isso é importante, vamos ter que validar isso.

> VAMOS TRANSFORMAR OS DADOS, DE MODO QUE ELES TENHAM UMA RELAÇÃO LINEAR, A MANEIRA MAIS FÁCIL DE FAZER ISSO É CASO SEUS ERROS (VARIÂNCIA) ASSUMA UMA CARACTERÍSTICA NORMAL.
## Transformações Comuns:
### Logarítmica:
- Y* = log(Y)
	Substitui cada valor pelo seu logaritmo. Pode ser base e, 10 ou 2 normalmente.
	Comum para grupos que tem médias grandes com variâncias grandes.
- Como não existe logaritmo de 0, é comum adicionar um 1 a todas observações.

### Transformação da Raiz Quadrada:
- Y* = $\sqrt{Y}$
	Como $\sqrt{0}$ é 0, então é necessário somar um valor pequeno como 0.5 ou 0.325 para todas as observações.

### Transformação da Arcoseno:
- Y* = arcoseno($\sqrt{Y}$) 
	Como $\sqrt{0}$ é 0, então é necessário somar um valor pequeno como 0.5 ou 0.325 para todas as observações.
	Útil para proporções binomiais. Os dados devem estar em uma escala 0 a 1.

### Transformação Inversa:
- Y* = $\frac{1}{Y}$
	Usado normalmente para dados que registram taxas.

### Transformação BOX-COX
Chamada de transformação de potência generalizada.
Uma família de expressão:
![[Pasted image 20250508192342.png]]
Sendo: v = graus de liberdade, n é o tamanho da amostra e st² é a variância dos dados de Y transformados.

Essa transformação retorna a melhor transformação normal possível de acordo com a conta realizada na eq (2).

De acordo com o $\lambda$ retornado pela eq(2) a eq(1) vai realizar transformações diferentes.

