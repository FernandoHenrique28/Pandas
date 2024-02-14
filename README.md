### Olá, vamos analisar um  dataset de engajamento do Instagram.
### Os dados foram coletados da plataforma kaggle, e estão disnponíveis na pasta chamada dataset.
### Basicamente, o dataset contém informações de uma página do Instagram, incluindo o tipo de postagem, data, número de curtidas, visualizações, número de pessoas presentes nas publicações e se a postagem é parte de uma campanha. Ele também inclui dados sobre as interações.

Para este projeto, foi usado apenas o módulo pandas.

Visualizando as primeiras cinco linhas:
![Visualizando as primeiras linhas](https://i.postimg.cc/Hxvz9rNb/Screenshot-27.png)

Visualizando as últimas cinco linhas.
[![Screenshot-28.png](https://i.postimg.cc/Y0c3s5pS/Screenshot-28.png)](https://postimg.cc/TL9gyH58)


Verificando as infomações:
[![Screenshot-29.png](https://i.postimg.cc/90V9TCmy/Screenshot-29.png)](https://postimg.cc/phGyMNnd)


Ao analisar rapidamente essas informações, parece que na coluna Carrossel existem apenas 8 valores não nulos, mas isso é um equívoco. Na realidade, os valores nulos correspondem a postagens que não são do tipo carrossel. Portanto, em vez de nulo, deveriam ser marcados como "N". Então teremos que atribuir o valor "N" para essa coluna.

## Tratando os valores nulos.
Atribuindo o valor N para a coluna Carrossel:
[![Screenshot-30.png](https://i.postimg.cc/76L8LT7z/Screenshot-30.png)](https://postimg.cc/bG4FCrmY).


## Agora vamos seguir para a parte estatística:
[![Screenshot-31.png](https://i.postimg.cc/TP3fKSvh/Screenshot-31.png)](https://postimg.cc/LJwr7xXM)

- A página do Instagram tem um bom engajamento, com uma média de mais de 12.000 curtidas e 189 comentários por postagem. 
- O número de curtidas e interações é bastante variável, com um desvio padrão superior a 8.000. 
- A maioria das postagens tem entre 5.492 e 17.621 curtidas, e entre 69 e 265 comentários. 
- Há algumas postagens com um número muito alto de curtidas e interações, e teremos que entender quais os motivos deste grande engajamento.

## Para melhorar a visualização dos dados, é interessante coloca-los em um gráfico de disperção que mostra a relação entre o número de curtidas e a data da postagem:
[![download.png](https://i.postimg.cc/R05w9ckP/download.png)](https://postimg.cc/xX5X3bTH)
Em relação ao tempo, não existe uma correlação positiva com o número de curtida e as datas de postagens, ou seja não existe um padrão.

A mesma coisa acontece quando analisamos os comentários em relação a data de postagem:
[![download-1.png](https://i.postimg.cc/FFVvxNF1/download-1.png)](https://postimg.cc/Rqh2SrHz)
Os gráficos e as informações estatítiscas não estão dizendo muita coisa pois existe uma grande dispersão entre curtidas e comentários.

## Buscando algum padrão usando outras colunas e informações.

É interessante nós analisarmos os cinco primeiros registros com mais e menos curtidas.
Cinco primeiros registros com mais curtidas:
[![Screenshot-32.png](https://i.postimg.cc/HxPQqfdM/Screenshot-32.png)](https://postimg.cc/VrnrMZSs)

Cinco primeiros registros com menos curtidas:
[![Screenshot-32.png](https://i.postimg.cc/HxPQqfdM/Screenshot-32.png)](https://postimg.cc/VrnrMZSs)

Insights:
- Podemos observar que no top 5 todas as postagens tinham pessoas e eram fotos de campanha.
- Nas 5 piores postagens, não haviam pessoas e nem eram postagens de campanhas.
- Isso pode ser um indicador que pessoas e campanhas tem relação com as quantidades de curtidas.

## Para melhor entender os dados, faz necessário usar o group by do pandas.
O `groupby` do Pandas permite agrupar linhas em um DataFrame com base em uma ou mais colunas e realizar cálculos agregados em cada grupo, sendo muito útil para  identificar  possíveis padrões e tendências.

[![Screenshot-35.png](https://i.postimg.cc/KjR6PkZM/Screenshot-35.png)](https://postimg.cc/bSfV8vSy)

Insight:

Note que o groupby já permite visualizar que as publicações que fazem parte de alguma campanha têm um alto engajamento, assim como as fotos que incluem pessoas. Isso pode ser um ponto a ser explorado pelo administrador da página, pois sugere que estratégias de marketing envolvendo campanhas e conteúdo com pessoas podem atrair mais atenção e interação dos seguidores. Portanto, seria interessante investir mais nessas abordagens para maximizar o impacto das postagens e fortalecer o relacionamento com a audiência.

[![Screenshot-36.png](https://i.postimg.cc/NGkDDfyy/Screenshot-36.png)](https://postimg.cc/8ssLPGmD)

Insight:

Postagens com pessoas engajam muito mais para essa marca, sendo 3 vezes maior de quando não tem pessoas

[![Screenshot-37.png](https://i.postimg.cc/154FF9D1/Screenshot-37.png)](https://postimg.cc/CzTdTpvc)

Insight:
Quando é uma postagem de campanha, o engajamento também é melhor!


[![Screenshot-38.png](https://i.postimg.cc/pTXrtZZM/Screenshot-38.png)](https://postimg.cc/WDCTG0C5)

Insight:

A média quando tem pessoas E é publicação de campanhas é de cerca de 19,4 mil curtidas, já quando é apenas pessoas (sem campanha passa para quase 10 mil e se não tiver pessoas chega no máximo a 5,9 mil mesmo em campanhas

Nesse caso a gente já consegue mostrar para a empresa a importância de incluir pessoas usando os seus produtos, o que gera um aumento considerável no engajamento.

[![Screenshot-39.png](https://i.postimg.cc/j5FxYr2y/Screenshot-39.png)](https://postimg.cc/tZFQFwhg)

E para finalizar, ao analisar a questão do vídeo, ele não parece mais tão ruim assim. Quando feito em campanha e usando pessoas ele teve um resultado bom, inclusive próximo a foto, o que poderia ter levado a média baixa é que só temos vídeo ou COM pessoa e COM campanha ou sem nenhum dos dois. 
Não existe nenhum vídeo com apenas um dos dois (pessoa ou campanha) Já IGTV, mesmo tendo pessoa, não teve um resultado tão bom.