# Predict-Time-Series for ROSSMAN

![image](https://user-images.githubusercontent.com/94385953/148453113-bb0cb6f0-159e-411c-8314-7f7093d8916f.png)

<b> AVISO: </b> Os dados desse projeto foram retirados de uma competição do Kaggle: https://www.kaggle.com/c/rossmann-store-sales/rules, a empresa seria a ROSSMAN uma empresa farmacêutica dos Estados Unidos. 

# Questão de Negócio 

Previsão de vendas das próximas 6 semanas.

# Problema de Negócio

O desafio seria implementar um modelo de Machine Learning que seria capaz de fazer uma previsão das 6 próximas semanas de receita da ROSSMAN. O CFO da Rossman fez essa solicitação porque ele necessita saber qual loja rende mais e qual rende menos. A Rossman fará uma manutenção em toda sua rede de lojas, com isso, a loja que tem a projeção de maior vendas nas próximas 6 semanas vão receber mais budget (dinheiro) na sua manutenção. 

# Método Ciclíco para solução do problema 

Utilizamos ao decorrer do projeto o método CRIPS-DS. O qual tem como premissa passar por todas etapas do projeto o mais rápido possível para chegar a solução sem perder tempo. No caso, podemos repetir o processo mais de uma vez para diminuir a margem de erro do nosso modelo. 

![image](https://user-images.githubusercontent.com/94385953/148467349-5f9b65f8-97e6-4396-b0e2-8a261d4fc290.png)

# Planejamento da Solução 

Com a primeira visualização da tabela abaixo foi possível termos uma visão geral do mínimo, máximo, média, mediana e outras variáveis

![image](https://user-images.githubusercontent.com/94385953/148455396-c475f749-dbc7-4a9e-b066-29d38a19c806.png)

Na nossa primeira análise verificamos que se tratava de 1115 lojas ao todo, e essas tem uma renda média de 5744 dólares, com 633 clientes em média indo a suas lojas. Nos dados aparecem os dias que a loja estavam fechadas por isso temos dias que as lojas não tiveram receita. 


# Criação das Hipóteses e Mapa mental

Antes de formularmos a hipótese. Tivemos a etapa de criação do mapa mental das possíveis KPI de cada unidade de trabalho dentro da ROSSMAN. O mapa mental foi interessante para termos uma ampla visão de quais unidades de negócios poderiam ter impacto no pedido do CFO e consequentemente na receita gerada na ROSSMAN. 
![image](https://user-images.githubusercontent.com/94385953/148467582-f9d7c35a-77c8-4b36-a0dc-d065c0206717.png)
Durante a etapa de validação de Hipóteses selecionamos 12 hipóteses para termos noção se seriam verdadeiras ou falsas. Com isso abaixo vamos comentar as hipóteses mais relevantes, que trazem maiores insights durante nossa análise: 


* <b> H1. Lojas com maior sortimentos deveriam vender mais. </b>
<b>FALSA</b> Lojas com maior variedade de produtos venderam menos segundo os dados. 
![image](https://user-images.githubusercontent.com/94385953/148467816-46810690-6ae3-4165-a335-4ce82d7a3bd5.png)


* <b> H2. Lojas com competidores mais próximos deveriam vender menos. </b>
<b>FALSA</b> Lojas com competidores mais próximos venderam MAIS. Isso se deve a fatores macroeconômicos. 
![image](https://user-images.githubusercontent.com/94385953/148467923-f758442d-8b71-4c44-b5a7-662aa03168c8.png)


* <b> H4. Lojas com promoções ativas por mais tempo deveriam vender mais. </b>
<b>FALSA</b> Lojas com promoções extendidas venderam menos do que lojas sem promoções extendidas. 
![image](https://user-images.githubusercontent.com/94385953/148468107-c3c4457e-46af-48b7-b672-525ecfe0abb0.png)
Como podemos ver em função do tempo as lojas sem promoção extendida segue uma projeção positiva, ou seja, aumento de vendas. Enquanto lojas com promoções extendidas uma projeção negativa. 


* <b> H10. Lojas deveriam vender mais no segundo semestre do ano. </b>
<b>FALSA</b> Lojas vendem menos depois do segundo semestre do ano. 
![image](https://user-images.githubusercontent.com/94385953/148468353-35024255-cd4e-4896-b305-99aa8809f1aa.png)
Precisamos entender porque ocorre esse fenômeno (caso se eu trabalhasse na ROSSMAN - solicitaria os dados de campanhas pagas para o pessoal de marketing e estudaria possíveis requisições durante essa época marketshare) 


* <b> H12. Lojas deveriam vender menos aos finais de semana. </b>
<b>VERDADEIRO</b> Lojas vendem menos aos finais de semana
![image](https://user-images.githubusercontent.com/94385953/148468590-6ddd8948-653b-4b6e-9c3c-732b2d1b7f49.png)



# Seleção de Variáveis para o modelo de Machine Learning 

O "Boruta" (biblioteca do Python), selecionou as seguintes variáveis: 

![image](https://user-images.githubusercontent.com/94385953/148468835-2804baa8-01f8-43df-b321-4cd6e82eb087.png)

Agora vamos rodar essas variáveis selecionadas para a próxima etapa - Machine Learning Modelling (O modelo de Machine Learning escolhido). 



# Machine Learning Modelling

Rodamos um modelo de Cross validation com 5 ciclos de validação para englobarmos maiores hipóteses possíveis. Não rodamos mais de 5 vezes por conta do CRISP que tem como premissa passar por tudo mais rapidamente para conseguirmos enxergar o todo. 

![image](https://user-images.githubusercontent.com/94385953/148469013-36d88a4e-c9c1-431a-820f-9dca54926965.png)

O modelo que escolhemos para utilizar na nossa predição foi o XGBoost Regressor, fiquei em dúvida nesse ou na Random Forest, como a Random Forest já utilizei antes optei por algo novo e eficiente.



# Modelo final utilizando a Random Search
O nosso RMSE (_Root Mean Squared Error_ - Erro médio Quadrado) foi de 1088.44, esse valor ficou um pouco mais alto por conta dos outliers, no segundo ciclo do CRISP podemos mudar alguns outliers para conseguirmos resultados melhores. 
O  MPE (_Mean Percentage Error_ - Erro médio percentual) foi de: 
![image](https://user-images.githubusercontent.com/94385953/148469263-9b196403-cd91-4e2e-aef1-6467c5966b83.png)
Equivalente a mais ou menos 19% com superestimando os dados. 



# Resultados | Previsão

Tivemos o seguinte gráfico de MAPE x Store: 
![image](https://user-images.githubusercontent.com/94385953/148469547-b6ae7b6b-952b-4ac4-9d47-725cf8e77cc3.png)
Ou seja o _erro médio absoluto percentual_ ficou controlado entre 0.2 e 0.1, somente em alguns casos tivemos picos de 0.5



## Lucro - Previssão

![image](https://user-images.githubusercontent.com/94385953/148469656-5f6a7245-8a24-4a5f-ae02-232b39c850fb.png)

A previsão ficou em R$ 287.260.416,00 teos ainda uma opção de pior cenário para tomadas de decisões mais protencionistas e temos a opção de melhor cenário. 

O nosso modelo de previsão ficou muito parelho com os resultados de vendas, a margem de erro ficou muito bem controlado. Abaixo temos a opção de um plot mostrando os resultados do modelo: 

![image](https://user-images.githubusercontent.com/94385953/148469819-78a31b1d-4f94-4663-bf1a-96d4c599e794.png)




### Exportação de um csv | Ao final da notebook temos a opção do CFO conseguir ver a previsão por lojas baixando um csv:

![image](https://user-images.githubusercontent.com/94385953/148469905-9e3b7dc5-d8ca-4db8-88e9-867e69fa9cc2.png)

Link para acesso: 




