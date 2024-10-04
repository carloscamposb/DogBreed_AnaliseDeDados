## Projeto: Dog Breeds - Extração, Tratamendo, Carregamento de Dados e Insights via Power BI

### Tecnologias Utilizadas:
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) <br>
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) <br>
![Power Bi](https://img.shields.io/badge/power_bi-F2C811?style=for-the-badge&logo=powerbi&logoColor=black) <br>

### Proposta:
Reealizar um projeto de Análise de Dados utilizando o Dataset "Breed (Raças)" do Kaggle focado em raças de cães, com o objetivo de aprimorar minhas habilidades 🤓. 
Deve ser utilizado o processo de ETL, utilizando Python e a biblioteca Pandas no Google Colab tratando os dados quando possível. 


### StoryTelling:
O projeto foi inspirado por uma empresa fictícia do setor pet, chamada Borcelle Dog's House
<div align=center>
  <img src='https://github.com/user-attachments/assets/a13c897a-d7b0-421c-bb04-391ed9061f5d' weight= 400 />
</div>






o que ajudou a definir as perguntas e direcionar as análises. As cores e a estrutura das visualizações foram elaboradas com esse cenário em mente. A experiência foi enriquecedora, permitindo a aplicação de diversas técnicas de análise e visualização de dados.









### Etapas:

Recentemente, realizei um projeto de análise de dados utilizando o dataset pequeno "Breed (Raças)" do Kaggle focado em raças de cães, com o objetivo de aprimorar minhas habilidades. No processo de ETL, utilizando Python e a biblioteca Pandas no Google Colab ajustei os nomes das colunas, separar valores, removi duplicatas, padronizei termos, alterei tipos de dados e excluir colunas desnecessárias para o estudo. Como o dataset não possuía valores nulos, o processo de limpeza foi simplificado. O arquivo final foi salvo no formato parquet.

No Power BI, estruturei o modelo de dados em três tabelas principais: Raças, Doenças e Características. Embora não tenha adotado um star schema, essa divisão facilitou a organização e a visualização das informações. As páginas do relatório foram organizadas para apresentar uma visão geral dos dados, a origem das raças, longevidade, doenças observadas e características comportamentais. Também agrupei as raças por porte (grande, médio e pequeno), destacando variações relevantes entre esses grupos.

Utilizei DAX para realizar sumarizações e calcular médias entre os valores das colunas. Uma análise interessante foi a correlação entre altura e longevidade. Após observar uma tendência no gráfico de dispersão, decidi calcular o coeficiente de correlação utilizando DAX, o que aprendi assistindo a vídeos tutoriais. O coeficiente obtido foi -0,63, indicando uma correlação negativa moderada: raças maiores tendem a viver menos, enquanto raças menores possuem maior longevidade. Essa análise confirmou uma tendência já conhecida, mas trouxe dados concretos para validação.

