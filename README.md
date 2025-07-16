# Trabalho2_AnaliseDados
*Trabalho 2 - Algoritmos de regressão e classificação.*
# Introdução
Aplicado os algoritimos de classificação: Regressão Logística, Árvores de Decisão, Random Forest, SVM (Máquinas de Vetores de Suporte), K-NN (K-Vizinhos Mais Próximos) e algoritimos de regressão: Regressão Linear, Árvore de Regressão, Random Forest Regressor, Support Vector Regressor (SVR) na base de dados de rotatividade de cliente com objetivo de obter qual algoritmo apresenta melhor resultado.

# Instruções
1. Adicionar arquivo "06_rotatividade_clientes_bancários".csv na pasta "/content/sample_data/06_rotatividade_clientes_bancários.csv" da maquina do colab;
2. Executar codigo na ordem apresentada no colab.

# Observações Iniciais:
O conjunto de dados contém as seguintes colunas: RowNumber, CustomerId, Surname, CreditScore, Geography, Gender, Age, Tenure, Balance, NumOfProducts, HasCrCard, IsActiveMember, EstimatedSalary e Exited.

**Material usado que nao foi apresentado em Aula**
Foi usado o Onehot encoding, com objetivo de transformar as colunas strings(Geography e Gender) de uma forma que os algoritmos matematicos entendem, nesse caso transforma em true/false.
Por exemplo: A variavel Geography virou duas variaves novas: Geography_Germany e Geography_Spain, caso  Geography_Spain igual a 1, entende que aquele dado é da Spain, o mesmo se aplica para Geography_Germany, caso as duas sejam falsas, a unica posibilidade é ser o 3 valor, nesse caso France, pois a base so possui 3 valores diferentes, Germany, France e Spain.

<img width="379" height="205" alt="image" src="https://github.com/user-attachments/assets/7a8e770f-ff4d-44f8-9c5d-fd98536ef422" />


# Variável Alvo:
**Classificação:** A coluna Exited será a variável alvo para os modelos de classificação, indicando se um cliente deixou o banco (1) ou não (0);

**Regressão:** A coluna CreditScore foi escolhida como variável alvo para os modelos de regressão.



