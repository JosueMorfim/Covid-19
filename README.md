# Covid-19
Cases/Death/Vaccine in Brazil, per state

# 1. Extração

Os dados foram retirados do site [DataSUS](https://opendatasus.saude.gov.br/dataset/covid-19-vacinacao/resource/301983f2-aa50-4977-8fec-cfab0806cb0b?inner_span=True).

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/6829bbcd-b9cd-4ff5-9714-af4836b5f7ca)

Os arquivos tinha em média 13GB cada, pois contém os dados de cada vacina/reforço de Covid-19 aplicadas. Como eu estava com pouco espaço de disco sobrando, tive que baixar os arquivos em duas partes, primeiro fiz o download do 1 ao 12, e posteriormente do 13 ao 20.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/95064f15-7110-4bd6-b8a2-0db4a19d071c)

# 2. Wrangling

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/21293527-0086-4862-8d92-f624aa559abd)

Nesta parte vamos abrir os arquivos em partes, e ja vamos fazer um pré processamento selecionando data, coluna de interesse, renomear colunas, e organizar tudo por date.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/9fa4e5f2-a2f3-4e34-9c66-247e32ceb6ce)


Vamos ver como esta nosso DataFrame depois do merge de todas as primeiras 12 partes. Com 206536626 de linhas.
Iremos também salvar a primeira parte processada dos dados em um csv chamado 'vacinasparte1.csv'.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/89c9eee7-a2e5-422e-9993-5cf5879a4a04)

Esse é o resultado as 8 partes finais. Com 137691919 de linhas.
Também ja iremos criar um csv chamado 'vacinasparte2.csv'.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/0cfe78fa-9dc6-43ba-a7ed-e39643195fa0)


Nesse momento vamos carregar os dois arquivos salvos, e realizar um merge no DataFrame vaccines_full.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/976bcd5e-b686-4e3f-8595-7202349ddb3b)

Agora nosso DataFrame esta com 344228546 linhas, e 7.7gb de dados.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/e477c6da-e4fd-4706-a9f6-6df6c603fd27)

Criamos um novo df apenas para ver os "tipos" de aplicação de vacinas existentes, para assim separamos os de interesse.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/7e512ae6-d66e-4b3e-a932-7052af78983a)

Vamos considerar como 1 dose, os que estão com nomeclatura 1ª Dose, Única e Dose. As doses de reforço não são consideradas como "Dose"" pelo ministério da saúde.
Já vamos aproveitar para reorganizar as colunas.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/2bc2f3b5-5c47-4ff0-bc0f-3463b23c4750)

Agora vamos agrupar os dados por estado e data e somar os valores.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/6b829dc0-daac-43f5-9f50-713aec2c4682)

Agora vamos salvar em um novo csv chamado 'vaccines_2021.csv'.

