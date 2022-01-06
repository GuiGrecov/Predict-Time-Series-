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

Agora que já temos o mapa mental vamos para a Criação de Hipóteses: 

* H1. 
