## Projeto: Dog Breeds - Extração, Tratamendo, Carregamento de Dados e Insights via Power BI

### Tecnologias Utilizadas:
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) <br>
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) <br>
![Power Bi](https://img.shields.io/badge/power_bi-F2C811?style=for-the-badge&logo=powerbi&logoColor=black) <br>

### Proposta:
Reealizar um projeto de Análise de Dados utilizando o Dataset ["Breed (Raças)" do Kaggle]( https://www.kaggle.com/datasets/marshuu/dog-breeds ) focado em raças de cães, com o objetivo de aprimorar minhas habilidades 🤓. 
Deve ser utilizado o processo de ETL, utilizando Python e a biblioteca Pandas no Google Colab tratando os dados quando possível. 

### Etapas de ETL: <br>
Utilizei o Google Colab para realizar o processo de ETL (Extract, Transform, Load) e começar a preparação dos dados. <br>

O banco de dados incluía informações sobre:

* **Breed:**	Nome da raça do cachorro <br>
* **Country of Origin:** País de origem <br>
* **Fur Color**: Cor do pêlo <br>
* **Height (in)**:	Tamanho em polegadas com menor e maior <br>
* **Color of Eyes**: Tipica cor do olho em raças de cachorro <br>
* **Longevity (yrs)**:	Logevidade dos cachorros em anos <br>
* **Character Traits**:	Caracteristicas típicas para a raça do cachorro <br>
* **Common Health Problems**:	Problemas comuns para a raça do cachorro <br>
<br>
💡Senti falta do peso e do gênero dos animais 

---
### Etapas de ETL <br>
#### Extract (Extração)

* O dataset foi baixado no formato CSV e carregado no Colab.<br>
Foi importado biblioteca necessária `pandas`,`chardat`,`numpy`
* Foi visualizado o formato (encoding) do dataset por meio do `chardat`. <br>
* Depois, foi separado as colunas usando o `sep=','` como separador. <br>
💡 Percebi que o dataset tinha 117 registros, mas ao avaliar os dados únicos, havia apenas 103 raças. Por isso, foi necessário retirar as duplicatas.

---
#### Transform (Transformação)
* Criei uma cópia do arquivo para manipulação. <br>
* Renomeei algumas colunas para ficarem menores, porém mais informativas <br>
* As colunas de Height (in) e Longevity (yrs) possuíam campos com menor e maior valores separados por hífen (-). <br>
💡 Decidi separar essas colunas. Para a coluna Height (in), separei em Height_min e Height_max, e por fim, a tabela Height(in) foi deletada. <br>
* Valores de Height estavam em polegadas e foram convertidos para centímetros e o tipo float. <br>
💡 Fiz o mesmo com Longevity, separando em Longevity_min e Longevity_max, e por fim, a tabela Longevity(in) foi deletada.<br>
* Foi padronizado valores de campos específicos para minúsculo usando o str.lower() para evitar erros na interpretação dos dados.<br>
💡 As tabelas Common Disease e Character Traits possuíam muitos valores separados por vírgula dentro do mesmo campo, então tomei a decisão de transformar cada valor em uma coluna na tabela, facilitando as análises, caso necessário, com granulações menores.<br>
* Foi separado a coluna de Common Disease e Character Traits e foi adicionado os valores binários para presença (1) e ausência (0).<br>
Apliquei o .drop para apagar colunas que julguei não serem necessárias para as análises.<br>
💡 As colunas eliminadas foram: Fur Color e Color of Eyes.<br>
----
#### Load (Carga)
* Por fim, o arquivo foi convertido em parquet para ser usado no Power BI. <br>
💡 Formato de arquivo mais leve
----
## PowerBI
### StoryTelling:
O projeto foi inspirado por uma empresa fictícia do setor pet, chamada Borcelle Dog's House 

<div align=center>
  <img src='https://github.com/user-attachments/assets/57eea564-f135-4f77-bca1-b9598fb0350c' weight= 400 />
</div>

Por meio dessa empresa foi definido as perguntas e direcionado as análises. As cores e a estrutura das visualizações foram elaboradas com esse cenário em mente.
No Power BI, pensei em uma empresa fictícia do setor de pets, especializada em cães, para definir as cores base e nortear as perguntas a serem respondidas. Isso ajudou a direcionar as análises, como as características e comportamentos que a empresa poderia estar interessada.

----
### Análises orientadas pelas perguntas:
<div align=center>
  <img src='https://github.com/user-attachments/assets/7e7ca9cb-5620-467e-acb7-80d758c5ba52' weight= 400 />
</div>

---

### Implementação de um modelo com três tabelas:
* Raças: id_raça, raça, origem, alturas e longevidades; <br>
* Doenças: id_raça, doenças, valor <br>
* Características: id_raça, características, valor <br>
💡Embora não tenha implementado um star schema completo, a separação dessas tabelas garantiu uma organização melhor. Além disso, alterei os nomes das colunas e células para o português, tornando as visualizações mais claras <br>

💡Ao agrupar as raças por porte (grande, médio e pequeno), percebi variações interessantes. Realizei uma breve pesquisa para definir os limites de tamanho, algo que inicialmente pensei que a empresa teria fornecido, mas que consegui ajustar <br>

💡EU utilizei DAX para realizar sumarizações e calcular médias entre os valores das colunas e outras analises.
> Uma análise interessante foi a correlação entre altura e longevidade. Após observar uma tendência no gráfico de dispersão, decidi calcular o coeficiente de correlação utilizando DAX, o que aprendi assistindo a vídeos tutoriais. O coeficiente obtido foi -0,63, indicando uma correlação negativa moderada: raças maiores tendem a viver menos, enquanto raças menores possuem maior longevidade. Essa análise confirmou uma tendência já conhecida, mas trouxe dados concretos para validação. <br>

---

Criei páginas no relatório focadas em:

* Overview do dataset,
* Origem das raças,
* Longevidade,
8 Doenças observadas,
* Características comportamentais.
-----

### Overview 
<div align=center>
  <img src='https://github.com/user-attachments/assets/db3ef418-f687-408b-836d-6050805d61eb' weight= 400 />
</div>

---

### Origem das raças
<div align=center>
  <img src='https://github.com/user-attachments/assets/ebdfa59c-37ff-4c45-ab6f-bdbe5854aa03' weight= 400 />
</div>

---

### Longevidade 
<div align=center>
  <img src='https://github.com/user-attachments/assets/42474b29-4936-44ab-a9b9-ad065c1b22d8' weight= 400 />
</div>


---

### Doenças Observadas
<div align=center>
  <img src='https://github.com/user-attachments/assets/c2bede28-98cd-44a8-878e-8f917fbe82a1' weight= 400 />
</div>

---


### Características Comportamentais
<div align=center>
  <img src='https://github.com/user-attachments/assets/d2383e37-23f7-4716-a9d2-f1126e1cd45c' weight= 400 />
</div>

----


## Conclusões ✏️
* Para casos de adoção focadas em raças de cachorro com a maior longevidade, provavelmente a preferência são cachorros de menor porte. Longevidade média (13-14 anos), cachorros de tamanho médio é uma boa aposta.
* Nesse Dataset a maior parte das origens das raças são europeias:
* As 5 maiores raças do Dataset são Europeias enquanto as 5 menores raças possuem uma distribuição continental maior
* Durante a convivência com o cãe é importante saber que há uma grande chance dele desenvolver problemas oculares, dentais e/ou de pele. Pois são doenças comuns mais recorrentes para as raças de cães desse estudo
* Valores únicos para doença foram observados para cancer em cães maiores e problemas respiratórios em cães menores
* Majoritariamente os cães que forem adotados podem apresentar tais características inteligencia, bom humor , serem energéticos, brincalhoes e leais.
* A caracteristica de ser energético foi mais atribuida a cães de pequeno porte:
   > Um cão pequeno e enérgico é ideal para pessoas ativas, com tempo para brincadeiras e exercícios regulares, e que vivem em espaços menores, como apartamentos. Ele se adapta bem a famílias e indivíduos que gostam de interação constante.
* Lealdade e inteligencia foram mais observadas em raças de cães de grande porte:
  > Ideais para pessoas que buscam companheiros protetores, fáceis de treinar, e que se dão bem com os integrantes da família. Eles exigem espaço e exercícios regulares para manter a saúde e o bem-estar. 
* Algumas raças de cães possuiam mais de 4 caracteristicas positivas associadas sendo 4 cães de grande porte e 1 de pequeno porte.
* O único caso de cão com menos características associadas foi observada para o Buldog Frânces, cão de pequeno porte com 3 características marcantes.




