# Covid-19
Cases/Death/Vaccine in Brazil, per state

# 1. Extração

Os dados foram retirados do site [DataSUS](https://opendatasus.saude.gov.br/dataset/covid-19-vacinacao/resource/301983f2-aa50-4977-8fec-cfab0806cb0b?inner_span=True).

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/8a8022c3-c446-4a37-9964-4334caffaae0)


Os arquivos tinha em média 13GB cada, pois contém os dados de cada vacina/reforço de Covid-19 aplicadas. Como eu estava com pouco espaço de disco sobrando, tive que baixar os arquivos em duas partes, primeiro fiz o download do 1 ao 12, e posteriormente do 13 ao 20.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/6b8914cd-eba4-400f-a3d9-411205a7027e)


# 2. Wrangling

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/63a050f0-f70f-4a3b-89c1-10844eb5c4c0)


Nesta parte vamos abrir os arquivos em partes, e ja vamos fazer um pré processamento selecionando data, coluna de interesse, renomear colunas, e organizar tudo por date.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/5cfa7950-b8ff-4bb0-8c03-e2d762c5366d)



Vamos ver como esta nosso DataFrame depois do concat de todas as primeiras 12 partes. Com 206536626 de linhas.
Iremos também salvar a primeira parte processada dos dados em um csv chamado 'vacinasparte1.csv'.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/a6a34658-d3ee-4863-8d0e-2007ebe1d3e6)


Esse é o resultado as 8 partes finais. Com 137691919 de linhas.
Também ja iremos criar um csv chamado 'vacinasparte2.csv'.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/2b3f4905-2dc3-4ba9-bef2-4b0ff35aeada)



Nesse momento vamos carregar os dois arquivos salvos, e realizar um concat no DataFrame vaccines_full.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/3ddb7cc3-be3b-44d8-966d-04668a829164)


Agora nosso DataFrame esta com 344228546 linhas, e 7.7gb de dados.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/8b57396e-8838-4e2a-9d6b-9b6d528020a6)


Criamos um novo df apenas para ver os "tipos" de aplicação de vacinas existentes, para assim separamos os de interesse.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/ee6a5dcd-10f9-4b0e-8fc8-95e754e662a1)


Vamos considerar como 1 dose, os que estão com nomeclatura 1ª Dose, Única e Dose. As doses de reforço não são consideradas como "Dose"" pelo ministério da saúde.
Já vamos aproveitar para reorganizar as colunas.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/218f2fd3-a3cd-49b5-acc5-f67383185cb8)


Agora vamos agrupar os dados por estado e data e somar os valores.

![image](https://github.com/JosueMorfim/Covid-19/assets/141301164/1148f282-42ad-4dfa-9737-6b3fe2b046be)


Agora vamos salvar em um novo csv chamado 'vaccines_2021.csv'.
