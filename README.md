## Projeto: Dog Breeds - Extração, Tratamendo, Carregamento de Dados e Insights via Power BI

### Tecnologias Utilizadas:
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) <br>
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) <br>
![Power Bi](https://img.shields.io/badge/power_bi-F2C811?style=for-the-badge&logo=powerbi&logoColor=black) <br>

### Proposta:
Reealizar um projeto de Análise de Dados utilizando o Dataset "Breed (Raças)" do Kaggle focado em raças de cães, com o objetivo de aprimorar minhas habilidades 🤓. 
Deve ser utilizado o processo de ETL, utilizando Python e a biblioteca Pandas no Google Colab tratando os dados quando possível. 

### Etapas de ETL:
Utilizei o Google Colab para realizar o processo de ETL (Extract, Transform, Load) e começar a preparação dos dados. <br>

O banco de dados incluía informações sobre:

**Breed:**	Nome da raça do cachorro <br>
**Country of Origin:** País de origem <br>
**Fur Color**: Cor do pêlo <br>
**Height (in)**:	Tamanho em polegadas com menor e maior <br>
**Color of Eyes**: Tipica cor do olho em raças de cachorro <br>
**Longevity (yrs)**:	Logevidade dos cachorros em anos <br>
**Character Traits**:	Caracteristicas típicas para a raça do cachorro <br>
**Common Health Problems**:	Problemas comuns para a raça do cachorro <br>

* O dataset foi baixado no formato csv e carregado no Colab <br>
* Foi importado bibliotecas necessárias `pandas`, `numpy` e `chardat` usando o `import` <br> 
* Foi visualizado o formato (encoding) do dataset por meio do `chardat` <br>
* Depois foi separado as colunas usando o `sep=','` como separador <br>
💡 Percebi que o dataset tinha 117 registros, mas ao avaliar os dados únicos, havia apenas 103 raças. Por isso foi necessário retirar as duplicatas <br> 
* Após isso, eu criei uma cópia do arquivo para manipulação <br>
* Renomeei algumas colunas para ficarem menores porém mais informativos: <br>
`dados_copia = dados_copia.rename(columns={'Country of Origin': 'Origin','Common Health Problems': 'Common Disease'})` <br>
* As colunas de **Height (in)** e **Longevity (yrs)** possuiam campos com menor e maior valores separados por hífen (-) <br>
💡Decidi separar essas colunas. Para coluna Height (in) separei em Height_min e Height_max e por fim a tabela Height(in) foi deletada. <br>
💡Fiz o mesmo com Longevidade separando em Longevity_min e Longevity_max e por fim a tabela Longevity(in) foi deletada. <br>



Primeiramente, separei os valores de longevidade e altura, que estavam em um formato de intervalo separado por um hífen (-), em duas colunas distintas: altura mínima e máxima e longevidade mínima e máxima.

Limpeza dos Dados
Ao verificar os tipos das variáveis, notei que todas estavam como categóricas. No entanto, percebi que o dataset tinha 117 registros, mas ao avaliar os dados únicos, havia apenas 103 raças. Removi as duplicatas baseando-me na coluna de raças.

Além disso, as colunas de doenças e traços característicos possuíam múltiplos atributos em um único campo, separados por vírgulas. Decidi transformar cada atributo em uma coluna separada, preenchendo-a com 1 para indicar presença e 0 para ausência. Por isso, alterei o tipo dessas novas colunas para inteiro, já que meu objetivo era utilizar essas informações em somatórias e análises posteriores.

Transformações Adicionais
Como a altura estava originalmente em polegadas, converti os valores para centímetros e os transformei em float, para facilitar o trabalho com gráficos e análises. Essa conversão estava especificada no dicionário de dados, então não vi necessidade de alterá-la diretamente na coluna.

Também observei que a coluna de doenças tinha alguns valores inconsistentes, com termos escritos em maiúsculas e minúsculas, o que estava sendo interpretado como categorias diferentes. Para padronizar, converti todos os valores para minúsculas.

Não havia valores nulos no dataset, o que simplificou o tratamento de dados. Ao final do processo de transformação, salvei o dataset no formato parquet, que é mais leve e otimiza a leitura e escrita de arquivos.




### StoryTelling:
O projeto foi inspirado por uma empresa fictícia do setor pet, chamada Borcelle Dog's House 

<div align=center>
  <img src='https://github.com/user-attachments/assets/a13c897a-d7b0-421c-bb04-391ed9061f5d' weight= 400 />
</div>

Por meio dessa empresa foi definido as perguntas e direcionado as análises. As cores e a estrutura das visualizações foram elaboradas com esse cenário em mente.








Recentemente, desenvolvi um projeto de análise de dados usando o dataset "Breed (Raças)" do Kaggle, focado em raças de cães. Utilizei o Google Colab para realizar o processo de ETL e o Power BI para criar visualizações.

Processo de ETL
O dataset continha informações como raça, longevidade, altura (em polegadas), cores dos olhos e pelos, doenças e características comportamentais (ex: brincalhão, inteligente). Primeiramente, separei os valores de longevidade e altura em quatro colunas: altura mínima e máxima e longevidade mínima e máxima, e converti a altura de polegadas para centímetros (formato float).

Percebi a falta de informações sobre peso e sexo, que seriam relevantes para uma análise mais completa. Além disso, a coluna de doenças e características continha várias informações separadas por vírgulas, então transformei cada atributo em colunas binárias (1 para presença e 0 para ausência). Após padronizar os textos em minúsculas, removi duplicatas, resultando em 103 raças únicas.

Antes de importar os dados para o Power BI, apaguei colunas que não seriam mais usadas, como cor dos olhos e pelos, e mudei os nomes das colunas para versões mais curtas e informativas. Também percebi que havia esquecido de adicionar a origem das raças como uma coluna importante para a análise, o que foi ajustado posteriormente. O dataset final foi salvo em parquet por sua eficiência.

Organização no Power BI
No Power BI, pensei em uma empresa fictícia do setor de pets, especializada em cães, para definir as cores base e nortear as perguntas a serem respondidas. Isso ajudou a direcionar as análises, como as características e comportamentos que a empresa poderia estar interessada.

Implementei um modelo com três tabelas:

Raças: id_raça, raça, origem, alturas e longevidades;
Doenças: id_raça, doenças, valor;
Características: id_raça, características, valor.
Embora não tenha implementado um star schema completo, a separação dessas tabelas garantiu uma organização melhor. Além disso, alterei os nomes das colunas e células para o português, tornando as visualizações mais claras.

Criei páginas no relatório focadas em:

Visão geral do dataset,
Origem das raças,
Longevidade,
Doenças observadas,
Características comportamentais.
Ao agrupar as raças por porte (grande, médio e pequeno), percebi variações interessantes. Realizei uma breve pesquisa para definir os limites de tamanho, algo que inicialmente pensei que a empresa teria fornecido, mas que consegui ajustar.





### Etapas:

Recentemente, realizei um projeto de análise de dados utilizando o dataset pequeno "Breed (Raças)" do Kaggle focado em raças de cães, com o objetivo de aprimorar minhas habilidades. No processo de ETL, utilizando Python e a biblioteca Pandas no Google Colab ajustei os nomes das colunas, separar valores, removi duplicatas, padronizei termos, alterei tipos de dados e excluir colunas desnecessárias para o estudo. Como o dataset não possuía valores nulos, o processo de limpeza foi simplificado. O arquivo final foi salvo no formato parquet.

No Power BI, estruturei o modelo de dados em três tabelas principais: Raças, Doenças e Características. Embora não tenha adotado um star schema, essa divisão facilitou a organização e a visualização das informações. As páginas do relatório foram organizadas para apresentar uma visão geral dos dados, a origem das raças, longevidade, doenças observadas e características comportamentais. Também agrupei as raças por porte (grande, médio e pequeno), destacando variações relevantes entre esses grupos.

Utilizei DAX para realizar sumarizações e calcular médias entre os valores das colunas. Uma análise interessante foi a correlação entre altura e longevidade. Após observar uma tendência no gráfico de dispersão, decidi calcular o coeficiente de correlação utilizando DAX, o que aprendi assistindo a vídeos tutoriais. O coeficiente obtido foi -0,63, indicando uma correlação negativa moderada: raças maiores tendem a viver menos, enquanto raças menores possuem maior longevidade. Essa análise confirmou uma tendência já conhecida, mas trouxe dados concretos para validação.

