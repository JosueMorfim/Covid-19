# Covid-19
Cases/Death/Vaccine in Brazil, per state

# 1. Extração

Os dados foram retirados do site [DataSUS](https://opendatasus.saude.gov.br/dataset/covid-19-vacinacao/resource/301983f2-aa50-4977-8fec-cfab0806cb0b?inner_span=True).

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/8ac34029-67e8-4fba-b20b-425ab3ea8e25)



Os arquivos tinha em média 13GB cada, pois contém os dados de cada vacina/reforço de Covid-19 aplicadas. Como eu estava com pouco espaço de disco sobrando, tive que baixar os arquivos em duas partes, primeiro fiz o download do 1 ao 12, e posteriormente do 13 ao 20.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/b7504cbc-3da5-4aa4-9ca2-3b8bef535b3f)



# 2. Wrangling

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/02f550f9-8280-47bb-b613-87fd7cd94581)



Nesta parte vamos abrir os arquivos em partes, e ja vamos fazer um pré processamento selecionando data, coluna de interesse, renomear colunas, e organizar tudo por date.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/002f51ce-d734-407c-b8ff-99bbdf01e209)




Vamos ver como esta nosso DataFrame depois do concat de todas as primeiras 12 partes. Com 206536626 de linhas.
Iremos também salvar a primeira parte processada dos dados em um csv chamado 'vacinasparte1.csv'.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/a8bccfd4-0c72-440f-86a7-b2c2291255b4)



Esse é o resultado as 8 partes finais. Com 137691919 de linhas.
Também ja iremos criar um csv chamado 'vacinasparte2.csv'.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/feb0065f-6001-4140-8c35-e51944897f4c)




Nesse momento vamos carregar os dois arquivos salvos, e realizar um concat no DataFrame vaccines_full.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/d23e6e26-efaf-44d3-b173-a512ce4ca31a)



Agora nosso DataFrame esta com 344228546 linhas, e 7.7gb de dados.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/a99d9cf9-6163-46d4-a917-b30418ebc719)



Criamos um novo df apenas para ver os "tipos" de aplicação de vacinas existentes, para assim separamos os de interesse.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/603e2ffc-1d20-4d14-887d-e0f99373b5a1)



Vamos considerar como 1 dose, os que estão com nomeclatura 1ª Dose, Única e Dose. As doses de reforço não são consideradas como "Dose"" pelo ministério da saúde.
Já vamos aproveitar para reorganizar as colunas.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/601f6257-719f-4953-adcf-ec75fb45f994)



Agora vamos agrupar os dados por estado e data e somar os valores.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/e4617fd1-8da5-4717-99ee-d8e609017377)



Agora vamos salvar em um novo csv chamado 'vaccines_2021.csv'.
