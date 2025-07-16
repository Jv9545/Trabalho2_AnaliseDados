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
Por exemplo: A variavel Geography virou duas variaves novas: Geography_Germany e Geography_Spain, caso  Geography_Spain igual a 1, entende que aquele dado é da Spain, o mesmo se aplica para Geography_Germany, caso as duas sejam falsas, a unica posibilidade é ser o 3º valor, nesse caso France, pois a base so possui 3 valores diferentes, Germany, France e Spain.

<img width="379" height="205" alt="image" src="https://github.com/user-attachments/assets/7a8e770f-ff4d-44f8-9c5d-fd98536ef422" />


# Variável Alvo:
**Classificação:** A coluna Exited será a variável alvo para os modelos de classificação, indicando se um cliente deixou o banco (1) ou não (0);

**Regressão:** A coluna CreditScore foi escolhida como variável alvo para os modelos de regressão.

# **Conclusão**
**Regreção**
--
**Melhor desempenho**: O modelo de Regressão Linear foi o melhor para previsão do creditScore, pois apresentou o menor RMSE (96.88). Isso significa que, o em média, as previsões do algoritmo foram de aproximadamente 97 pontos. O fato que regressão linear é melhor e mais indicado para dados que se apresentam lineares foi o motivo que seu resultado superior aos demais algorimos, mesmo que os outros algoritmos sejam mais complexos

**Pior Desempenho:** A Árvore de Regressão teve um desempenho muito ruim, com um erro médio de 141 pontos. Isso é esperado, pois árvores de decisão únicas tendem a ser instáveis e cometer mais erros do que modelos mais robustos como o Random Forest.

**Gráfico de Distribuição de Erros:** O grafico usado para apresentar de forma visual os resultados de todos os 4 algoritmos. Percebese que quanto mais "pontudo" o grafico melhor o resultado, enquanto que linhas mais "espalhada" pior. Que é o caso da linha azul(Regressão Linear) e laranja(Árvore de Regressão) respectivamente.


**Clasificação**
-
**Melhor Resultado**: O Random Forest e o SVM foram os melhores modelos quando avaliado a suas acurácias, ambos com 86% de acurácia. A diferença entre ele é que o Random Forest se destaca ligeiramente com o maior F1-Score (0.76) e um bom Recall (0.73). Apresentando um equilibrio:: acerta bastante quem vai sair, sem acusar muitos clientes fiéis de forma errada. Já o SVM tem um pouco mais de precisão(85%), mas seu Recall mais baixo (0.70) indica que ele "deixa passar" mais clientes que realmente saem do que o Random Forest.

**Pior resultado:** A Regressão Logística teve o pior desempenho geral com o F1-Score de 0.61. O principal problema é que ela não consegue identificar bem os clientes que de fato saíram.

# **Defesa dos Hiperparametros**
**Regressão Logística (LogisticRegression(max_iter=200)):** O padrão é max_iter=100, aumentar o número máximo de iterações para 200 é uma prática comum para garantir que o otimizador do modelo tenha tempo necessario para encontrar uma solução e garantindo a estabilidade do treinamento.

**Árvore de Decisão (DecisionTreeClassifier(random_state=42)):** Foram utilizados os parâmetros padrão para avaliar o desempenho base do modelo. random_state garante a reprodutibilidade.

**Random Forest (RandomForestClassifier(n_estimators=100, random_state=42)):**  A escolha segue os valores padrão da biblioteca, que são um ponto de partida robusto e amplamente utilizado na comunidade.

**SVM (SVC(kernel='rbf')):** Foi utilizado o valor padrão. O kernel rbf (Radial Basis Function) é extremamente versátil e poderoso, capaz de encontrar relações não-lineares complexas, sendo a escolha inicial na maioria dos problemas de classificação.

**K-NN (KNeighborsClassifier(n_neighbors=5)):** O valor n_neighbors=5 é o padrão do Scikit-learn. É uma escolha balanceada que considera uma vizinhança local para a classificação sem ser excessivamente sensível a ruídos (como seria com k=1) ou excessivamente generalista.
