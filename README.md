# 1.Business Problem
O dataset utilizado neste projeto contém 31 variáveis e registra transações de cartões de crédito realizadas em setembro de 2013 por titulares europeus. As transações, ocorridas em um período de dois dias, totalizam 284.807, das quais 492 foram fraudulentas, representando apenas 0,172% do total. 

O objetivo do projeto era construir um modelo de classificação para prever se uma transação é fraudulenta ou não. Devido ao desequilíbrio das classes, utilizou-se a Área sob a Curva de Recuperação de Precisão (AUPRC) para medir a precisão do modelo, garantindo a detecção eficaz das fraudes.

# 2.Context Analysis
Esse conjunto de dados contém apenas variáveis ​​de entrada numéricas que são o resultado de uma transformação PCA. Infelizmente, devido a questões de confidencialidade, não foi possível obter os recursos originais e mais informações básicas sobre os dados. 
As features V1, V2,… V28 foram obtidas com PCA, as únicas features que não foram transformados com PCA foram 'Time' e 'Amount'. A variável 'Time' contém os segundos decorridos entre cada transação e a primeira transação no conjunto de dados. A variável 'Amount' é o valor da transação. A feature 'Class' é a variável resposta e assume valor 1 em caso de fraude e 0 caso contrário.

# 3. Solution Strategy
Para este projeto, o método CRISP-DM foi utilizado, contando com alguns dos 10 passos abaixo: 

1 - Problema de Negócio: Identificar o problema de negócio a ser solucionado;

2 - Entendimento do Problema de Negócio: Compreender a motivação, a causa e propor a estratégia de solução para este problema.

3 - Coleta de Dados: Os dados foram obtidos através do Kaggle. (Credit Card Fraud Detection)

4 - Limpeza dos Dados: Consiste em renomear colunas, converter as variáveis para seus tipos corretos, verificar e preencher NA´s quando necessário, seguindo as motivações do negócio, além de fornecer um breve resumo descritivo dos dados. Neste dataset não foi necessário realizar limpezas ou transformações.

5 - Exploração dos Dados: Esta etapa busca analisar e compreender as variáveis que impactam a variável resposta do projeto. Como foi utilizado dados anonimizados a possibilidade de entendimento profundo das variáveis reduz significadamente. 

6 - Modelagem dos Dados: Esta etapa é fundamental para preparar os dados conforme os requisitos dos algoritmos de Machine Learning.
Neste dataset, não foi necessário pré-processamentos, pois todas as colunas eram numéricas.

7 - Seleção de Features: Esta etapa do projeto filtra as features mais relevantes para o treinamento de Machine Learning que vem a seguir. Não é interessante para o projeto ter um número muito grande de colunas que não impactam na explicação do problema estudado.

8 - Machine Learning: Em seguida, os dados preparados são treinados em diversos algoritmos de Machine Learning, a fim de obter o melhor modelo para explicar o fenômeno.  Realizados esses procedimentos, aplica-se o Hyperparameter Fine Tuning para o modelo que apresentar melhor resultado, encontrando os melhores parâmetros para o algoritmo e maximizando ainda mais a performance do modelo.

9 - Avaliação do Algoritmo: Aqui, avalia-se o algoritmo com os dados de teste previamente separados, de acordo com métricas alinhadas ao tipo de aprendizado dos modelos de Machine Learning. Ao final, a parte mais importante: traduzir a performance do algoritmo para resultados em termos de negócio e receitas para a empresa e mostrar a diferença, além do impacto que a utilização das técnicas trabalhadas aqui proporcionam para o desenvolvimento da empresa.

10 - Modelo em Produção: Por fim, o modelo avaliado é publicado (Deploy). Neste caso não foi feito um deploy do modelo.

# 5. Insights
**Curva Precision-Recall**

Ao visualizar o trade-off entre precisão e recall, podemos verificar um bom equilibrio entre eles utilizando o modelo XGBoostClassifier.
![output](https://github.com/pammagalhaes/fraud_detection/assets/113152370/749e1ecc-ed60-40a2-a353-84581d16ee42)

**Distribuição do Valor das Transações por Classe**

No gráfico abaixo, podemos verificar que transações fraudulentas ocorrem em sua maioria das vezes em valores menores que 5000.

**ATENÇÃO:** A aplicação da Análise de Componentes Principais (PCA) nos dados introduz uma transformação matemática que pode afetar a interpretação literal dos valores resultantes. Sendo assim, a interpretação literal dos valores dos componentes principais como "reais" pode ser enganosa, pois eles representam uma combinação linear das variáveis originais.
![output2](https://github.com/pammagalhaes/fraud_detection/assets/113152370/475cf60b-d3e4-424f-8d62-93feb02667ef)


# 6. Machine Learning Model

Foram desenvolvidos e treinados três modelos de Aprendizado de Máquina para identificar o algoritmo mais eficaz em descrever e resolver o problema proposto:

**DecisionTreeClassifier**

**XGBoostClassifier**

**LogisticRegression**

Cada modelo foi treinado e avaliado usando métricas como **Precision**, **Recall** e **AUC-RP**. 

O modelo final escolhido foi o **XGBoostClassifier**, devido a um bom desempenho na análise das métricas e por ser um modelo que geralmente tem um desempenho melhor com dados desbalanceados.
Como resultado foi alcançado uma **AUC-RP** de 85%, AUC-RP é a métrica mais utilizada em problemas de classificação binários desbalanceados.
Quanto mais alta essa métrica, melhor o resultado do modelo, ou seja, maior precisão e recall combinados.
