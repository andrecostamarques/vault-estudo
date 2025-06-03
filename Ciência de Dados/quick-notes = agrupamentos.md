agrupamento hierarquico -> um grupo dentro do outro
agrupamento particional -> um grupo fora do outro

inormação dento do grupo -> validas
informacao fora do grupo -> diferente


Hierarquico:
- Aglomerativo -> bottom-up
	- Cada ponto é um grupo
	- os grupos se combinam 
	- precisa saber o quao perto estao
- Divisivo -> top-down
	- todos sao um grupo
	- se separa a cada etapa
	- qual grupo vai ser dividio

## aglomerativo:
há k = n grupos
no fim todos estão no mesmo grupo

no inicio cada grupo é individual, não tem variância

a escolha da qnt de grupos é subjetiva (n_clusters)

#### Métodos:
vizinho mais proximo
vizinho mais distante
distancia media
centroid 
ward


1. Vizinho mais proximo:
	- A distancia é definita pelos mais proximos
	- a cada passo, os dois (grupos) mais proximos se juntam 
	- utiliza distancia euclidiana (raiz quadrada)
	- junta os grupos e pega o menor valor do grupo

2. Vizinho mais distânte:
   - a similaridade é dado pela mais distante
   - é calculada a maior distancia entre todos, junta os menores
   - junta os grupos e pega o maior valor do grupo

1. distancia media 
- distancia entre os grupos é a media da distancia entre todos
- pega a media de todos juntos
- depois pega a menor

1. Centroid
- distancia medida entre vetores de media de grupos, centroides dos grupos
- media a - media b)T * media a - media b
- exige mais computacao que so outros
- dificil ignorar

1. ward:
- minima variancia
- calcaula a soma de quadrados dentro de cada grupo
- combina os dois grupos que tiver a menor soma dos quadrados


resumo:
mtos metodos, nenhum melhor
diferentes metodos diferentes resultados
vizinho mais distante tem mais outliers
distancia media tem menor variancia interna
ward grupos com elementos mais parecidos
boas praticas comparar varios metodos entre si


### metodos nao hierarquicos
particionar n em k grupos homongeneos entre si e heterogeneos entre os grupos
numero k deve ser escolhido antes
deve ter algum criterio de partica
nao da pra avaliar as particpes, por isso é no olho
metodos nao hierarquico é em matriz de dados
nao da pra construir dendogramas

kmedias (kmeans)
- mais conhecidos
- cada observacao é um grupo de centroid 
- acha um grupo que minimiza a soma dos quadrados
- calcular centroides
- colocar os valores mais perto dos centroids
- recalcular os centroies
- repetir até todos estarem juntos
- inicio dos centroids aleatorio
- ruim pq tem q decidir valor de k antes
- pode ter q correr mtas vezes ate achar um centroid bom
- 