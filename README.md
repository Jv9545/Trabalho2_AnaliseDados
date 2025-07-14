# Trabalho2_AnaliseDados
Trabalho 2 - Algoritmos de regressão e classificação.
# Introdução
Aplicado os algoritimos de classificação: Regressão Logística, Árvores de Decisão, Random Forest, SVM (Máquinas de Vetores de Suporte), K-NN (K-Vizinhos Mais Próximos) e algoritimos de regressão: Regressão Linear, Árvore de Regressão, Random Forest Regressor, Support Vector Regressor (SVR) na base de dados de rotatividade de cliente com objetivo de obter qual algoritmo apresenta melhor resultado.

# Instruções
1. Adicionar arquivo "06_rotatividade_clientes_bancários".csv na pasta "/content/sample_data/06_rotatividade_clientes_bancários.csv" da maquina do colab;
2. Executar codigo na ordem apresentada no colab.

# Observações Iniciais:
O conjunto de dados contém as seguintes colunas: RowNumber, CustomerId, Surname, CreditScore, Geography, Gender, Age, Tenure, Balance, NumOfProducts, HasCrCard, IsActiveMember, EstimatedSalary e Exited.

# Variável Alvo:
Classificação: A coluna Exited será a variável alvo para os modelos de classificação, indicando se um cliente deixou o banco (1) ou não (0);
Regressão: A coluna CreditScore foi escolhida como variável alvo para os modelos de regressão.
