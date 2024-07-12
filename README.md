# Truck Air System Project

![imagem](img/img1.jpeg)

---

# 1. Business Problem

Uma nova empresa de consultoria em ciência de dados foi contratada para solucionar e aprimorar o planejamento de manutenção de uma empresa terceirizada de transporte. A empresa mantém um número médio de caminhões em sua frota para fazer entregas em todo o país. Porém, nos últimos 3 anos vem percebendo um grande aumento nos gastos relacionados à manutenção do sistema de ar de seus veículos, mesmo com o tamanho da sua frota relativamente constante ao longo do período. O custo de manutenção deste sistema específico é mostrado abaixo em dólares:

![imagem](img/img2.png)

Neste sentido, o trabalho do cientista de dados é criar um modelo preditivo na tentativa de diminuir o custo anual para 2022. Esses custos são gerados devido aos seguintes critérios:

- Caso um caminhão seja enviado para manutenção, mas não apresente nenhum defeito nesse sistema, serão cobrados cerca de 10 dólares pelo tempo gasto na inspeção pela equipe especializada.
- Caso um caminhão seja enviado para manutenção e apresente defeito neste sistema, serão cobrados 25 dólares para realizar o serviço de reparo preventivo.

- Caso um caminhão com defeito no sistema de ar não seja enviado diretamente para manutenção, a empresa paga 500 dólares para realizar a manutenção corretiva, considerando mão de obra, reposição de peças e outros possíveis inconvenientes.

# 2. Challenge Activities

#### 1. What steps would you take to solve this problem? Please describe as completely and clearly as possible all the steps that you see as essential for solving the problem.

Para resolver este problema é fundamental seguir o método CRISP nas seguintes etapas:
1. Compreender o Problema de Negócio
2. Importar/coletar os dados
3. Limpar os Dados
4. Realizar Análise Exploratória dos Dados
5. Preparação dos Dados
6. Selecionar as variáveis mais relevantes
7. Treinar algoritmos de Machine Learning
8. Avaliar a performance desses algoritmos
9. Ajustar os hiperparâmetros
10. Gerar a Matriz de Confusão
11. Avaliar o impacto e a solução final

#### 2. Which technical data science metric would you use to solve this challenge? Ex: absolute error, rmse, etc. 

Por se tratar de um projeto de classificação, as métricas usadas serão Precisão, Recall, F1-Score e área sob a curva ROC. O modelo será ajustado nos hiperparâmetros a fim de maximizar a área sob a curva ROC.

#### 3. Which business metric would you use to solve the challenge?

A métrica de negócio que será utilizada aqui será a Redução de Custos. Tendo ciência dos custos dos últimos anos com o sistema de ar condicionado, o objetivo aqui é reduzir este custo anual. 

#### 4. How do technical metrics relate to the business metrics?

As métricas técnicas se relacionam com as métricas de negócio de forma que o ajuste dos valores das métricas técnicas vão impactar no custo, no caso a métrica de negócio. Em suma, a métrica técnica representa a qualidade do modelo e, quanto mais qualidade e performance deste modelo, melhor será para a métrica de negócio, ou seja, diminuir o custo.

#### 5. What types of analyzes would you like to perform on the customer database?

Podem ser realizadas as análises descritivas, fazendo médias, medianas, desvios padrão. Representação por gráficos, histogramas, boxplots e histplots. Além disso, podemos fazer análises bivariadas, como correlações entre as features e heatmaps. E também análises preditivas, utilizando algoritmos de machine learning.

#### 6. What techniques would you use to reduce the dimensionality of the problem? 

Pode ser usada a técnica do PCA, recomendada para datasets com centenas ou até milhares de variáveis. Para reduzir a dimensionalidade do problema podemos utilizar métodos para filtrar as melhores features, ou seja, as variáveis capazes de descrever melhor o problema de negócio. Além disso, usaremos também modelos baseados em Árvore, como Random forest, LGBM e XGboost. Esses modelos são interessantes para isso pois em dados com alta dimensionalidade, há algumas características não tão importantes para a predição que podem atrapalhar o modelo. Assi, Os algoritmos baseados em árvore ajudam a eliminar essas características irrelevantes, reduzindo o número total de características.

#### 7. What techniques would you use to select variables for your predictive model?

Podem ser usadas a correlação, feature importance, utilização do método Boruta.

#### 8. What predictive models would you use or test for this problem? Please indicate at least 3.

Pra esse problema nós podemos usar a Random Forest, Extra Tree, o LGBM e o XGBoost.

#### 9. How would you rate which of the trained models is the best?

A avaliação é feita a partir das métricas apresentadas acima. Neste caso, a área sob a curva ROC é uma boa métrica pra mostrar o quão bem performou o algoritmo. Além disso, tendo ciência do risco de overfitting, usamos também o cross-validation para cada um dos modelos. 

#### 10. How would you explain the result of your model? Is it possible to know which variables are most important?

Para explicar o resultado deste modelo, depende de quem são nossos interlocutores. Por exemplo, para uma equipe técnica é interessante falar sobre as métricas mais técnicas como Precisão x Recall, curva ROC etc. Já para explicar para clientes ou outras pessoas de outros times na empresa, a abordagem deve ser mais voltada para o negócio, falando mais sobre os custos, sobre como cada resultado em cada cenário vai impactar de forma diferente nos custos. Em relação Às variáveis, podemos utilizar árvores de decisão, feature importance, correlações para saber quais variáveis tem mais relação com o a variável alvo estudada. 

#### 11. How would you assess the financial impact of the proposed model?

O impacto financeito é avaliado comparando-se o custo dos anos anteriores com o custo atual que o modelo está propondo. Em suma, um baseline para comparação, além de poder calcular a porcentagem de queda em relação aos custos anteriores. 

#### 12. What techniques would you use to perform the hyperparameter optimization of the chosen model?

A técnica utilizada será o Optuna. O optuna faz um estudo pegando por intervalo escolhido de cada parâmetro também escolhido. Também é possível escolher o número de interações que ele vai percorrer. 

#### 13. What risks or precautions would you present to the customer before putting this model into production?

A principal recomendação para o cliente é em relação a performance da produção. Pode ser que o desempenho mostrado aqui tenha alterações na produção. Portanto, o modelo deve ser monitorado continuamente. Este fato, claro, impacta diretamente nos resultados de negócio, que também devem ser avaliados continuamente. Além disso, o modelo também deve ser preparado para ter segurança necessária em relação a proteção de dados e perigos em relação a manipulação de dados. 

#### 14. If your predictive model is approved, how would you put it into production?

Inicialmente o modelo deve ser salvo utilizando Pickle. Em seguida, pode ser necessária a construção de uma API que permita que o modelo seja acessado por outros usuários e outras aplicações, atuando como um "intermediário" entre as predições e o usuário que vai acessá-las. Em seguida criar conteineres que inclua a API e utilizar serviços pra gerenciá-los.

#### 15. If the model is in production, how would you monitor it?

O modelo pode ser monitorado por ferramentas como Prometheus e Grafana, que monitoram a performance do modelo e da API. É importante também configurar alertas em caso de problemas de performance ou ainda outros eventuais erros que possam acontecer.

#### 16. If the model is in production, how would you know when to retrain it?

O modelo deve ser retreinado quando ele passa a não desempenhar bem, em relação a como vinha desempenhando. Portanto, as métricas devem continuar sendo avaliadas e monitoradas, bem como a matriz de confusão, que quando apresentar um número mais elevado que o esperado de falsos negativos e falsos positivos deve-se avaliar a possibilidade do retreino. O retreino também acontece com entrada de novos dados, novas features, depois de recortes e intervalos de tempo significativos ou ainda outros fatores capazes de alterar o desempenho do modelo. 

# 3. Solution Strategy 

A estratégia utilizada foi o método CRISP, dividido em 11 ações:

![imagem](img/img3.png)

1. Compreender o Problema de Negócio
2. Importar/coletar os dados
3. Limpar os Dados
4. Realizar Análise Exploratória dos Dados
5. Preparação dos Dados
6. Selecionar as variáveis mais relevantes
7. Treinar algoritmos de Machine Learning
8. Avaliar a performance desses algoritmos
9. Ajustar os hiperparâmetros
10. Gerar a Matriz de Confusão
11. Avaliar o impacto e a solução final

# 4. Top Insight

Os dados mostram que dos 60 mil caminhões com algum defeito, apenas mil são defeitos no sistema de ar. Ou seja, aproximadamente, 1.6% do total de caminhões. 

![imagem](img/img4.png)

Já para os dados de 2022 há uma incidência um pouco maior, dos 16 mil caminhões, 375 estão com defeito no sistema de ar, representando 2,34% do total.

# 5. Machine Learning Model Applied 

Após a preparação de dados, o objetivo era verificar quais features são mais relevantes para o modelo. Como o resultado foi bem equilibrado e não se verificou melhora no desempenho dos treinamentos dos algoritmos, optou-se por realizar o treinamento final com todas as variáveis. 

Além disso, foi utilizada a técnica do PCA(Principal Component Analysi), que é uma técnica de redução de dimensionalidade capaz de transformar um conjunto de variáveis em um conjunto menor de variáveis. No entanto, também não se verificou melhoria no resultado final.

Foram treinados 4 modelos de Aprendizado de Máquina com objetivo de encontrar o melhor algoritmo que descreva e explique o problema proposto:

- Random Forest Classifier
- Light Gradient Boosting Machine Classifier
- Extra Trees Classifier
- XGBoost Classifier

Algumas métricas foram analisadas para estudar os modelos: Precision, Recall e Roc_auc, F1-Score e Log-loss.

#### Precision: 
Proporção de caminhões corretamente identificados como defeituosos, entre todos os caminhões classificados como defeituosos.

#### Recall: 
Proporção de caminhões corretamente identificados como defeituosos no entre todos os caminhões que realmente têm defeito.

#### Área Sob a Curva ROC
Mede a capacidade do modelo de distinguir entre caminhões com e sem defeito.

#### F1-Score: 
Média harmônica entre precisão e recall, equilibrando os dois aspectos.

#### Log-loss: 
Calcula a penalidade para prever a probabilidade de um caminhão ter ou não defeito. Quanto mais próximo de 0, melhor. Isso significa que as previsões de probabilidade do modelo estão mais alinhadas com os valores reais, indicando um desempenho melhor.

Após todos os modelos treinados, aquele que apresentou o melhor desempenho foi o XGBoot Classifier, com os seguintes resultados:

![imagem](img/img5.png)

# 6. Business Result

Após a utilização do Optuna, que maximizou os parâmetros para o maior valor de área sob a curva ROC, descobriu-se que o treshold que minimiza os custos baseando-se na condições apresentadas é aproximadamente 2%. Assim, foi possível construir a Matriz de Confusão, que pode ser analisada da seguinte maneira:

#### True Negatives (TN): 15241
Estes são os casos em que o modelo previu a classe negativa corretamente. Ou seja, o modelo previu que 15241 caminhões não tem defeitos no sistema de ar e realmente não tem.

#### False Negatives (FN): 11
Estes são os casos em que o modelo previu a classe negativa incorretamente. Ou seja, o modelo previu que 11 caminhões não apresentavam defeitos no sistema de ar, mas que estavam sim defeituosos. 

#### False Positives (FP): 384
Estes são os casos em que o modelo previu a classe positiva incorretamente. Ou seja, o modelo previu que 384 caminhões apresentavam defeitos, mas que na verdade não estavam defeituosos.

#### True Positives (TP): 364
Estes são os casos em que o modelo previu a classe positiva corretamente. Ou seja, o modelo previu que 364 caminhões apresentavam defeitos no sistema de ar e realmente estavam defeituosos. 

## Custos por cenário

- Segundo enunciado, caso um caminhão seja enviado para manutenção, mas não apresente nenhum defeito nesse sistema, serão cobrados cerca de 10 dólares pelo tempo gasto na inspeção pela equipe especializada. Portanto, como o modelo vai apresentar 384 caminhões como defeituosos (mas que não estão), estes caminhões serão enviados para manutenção e assim será cobrado 10 dólares de cada um. Logo: 10*384 = $ 3840

- Caso um caminhão seja enviado para manutenção e apresente defeito neste sistema, serão cobrados 25 dólares para realizar o serviço de reparo preventivo. Portanto, como o modelo vai apresentar 364 caminhões como defeituosos(e estão realmente), será cobrado 25 dólares pra cada caminhão pro reparo preventivo. Logo: 25*364 = $ 9100

- Caso um caminhão com defeito no sistema de ar não seja enviado diretamente para manutenção, a empresa paga 500 dólares para realizar a manutenção corretiva do mesmo, considerando mão de obra, reposição de peças e outros possíveis inconvenientes. Portanto, como o modelo vai apresentar 11 caminhões sem defeitos no sistema de ar (mas que estão com defeito), estes caminhões não serão enviados para manuntenção e a empresa terá que gastar 500 dólares para realizar uma manutenção corretiva. Logo: 500*11 = $ 5500.

## Custo Total Final em 2022

Assim, o custo total pro ano de 2022 é de: 3840 + 9100 + 5500 = 18.440 dólares

Este valor é menor que o valor de todos os anos registrados desde 2016. Além disso, é 50% mais baixo do que o valor do último ano apresentado (2020).

# 7. Conclusions

Os resultados de negócio mostram que o objetivo do projeto foi alcançado e, portanto, a empresa terá uma redução de 50% no seu custo, alcançando um valor para o ano estudado menor do que o menor registro histórico, de acordo com o gráfico apresentado na introdução deste relatório. 

# 8. Lessons Learned e Next Steps 

Nas próximas etapas do ciclo CRISP podem ser incrementados:

- Análise variável a variável dos outliers.
- Testar outros algoritmos de Machine Learning
- Criar outras features na etapa de Featuring Engineering

# 9. References

- O enunciado do projeto, os datasets e o gráfico introdutório são de posse da BIX Tecnologia.
- A imagem de capa: [Pexels](https://www.pexels.com/pt-br/foto/caminhao-basculante-vermelho-perto-de-rochas-arquivadas-sob-ceu-nublado-1044290/)
- Imagem CRISP: [Arte dos Dados](https://artedosdados.blogspot.com/2013/12/mineracao-de-dados-e-o-crisp-dm-data.html)