# Trabalho 2 - Análise de Dados

*Trabalho 2 - Algoritmos de regressão e classificação.*

# Introdução

Foram aplicados os algoritmos de classificação: Regressão Logística, Árvores de Decisão, Random Forest, SVM (Máquinas de Vetores de Suporte), K-NN (K-Vizinhos Mais Próximos) e os algoritmos de regressão: Regressão Linear, Árvore de Regressão, Random Forest Regressor e Support Vector Regressor (SVR) na base de dados de rotatividade de clientes bancários, com o objetivo de obter qual algoritmo apresenta o melhor resultado.

# Instruções

1.  Adicionar o arquivo "06\_rotatividade\_clientes\_bancários.csv" na pasta "/content/sample\_data/" da máquina do Colab.
2.  Executar o código na ordem apresentada no Colab.

# Observações Iniciais

O conjunto de dados contém as seguintes colunas: `RowNumber`, `CustomerId`, `Surname`, `CreditScore`, `Geography`, `Gender`, `Age`, `Tenure`, `Balance`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`, `EstimatedSalary` e `Exited`.

**Material usado que não foi apresentado em Aula**
Foi usado o One-Hot Encoding, com o objetivo de transformar as colunas de texto (`Geography` e `Gender`) de uma forma que os algoritmos matemáticos entendam. Nesse caso, ele as transforma em valores binários (verdadeiro/falso).
Por exemplo: a variável `Geography` foi transformada em duas novas variáveis: `Geography_Germany` e `Geography_Spain`. Caso `Geography_Spain` seja igual a 1, entende-se que aquele dado é da Espanha. O mesmo se aplica para `Geography_Germany`. Caso ambas sejam falsas, a única possibilidade é ser o terceiro valor, neste caso, França, pois a base de dados só possui três valores distintos para essa coluna: Alemanha, França e Espanha.

<img width="355" height="183" alt="image" src="https://github.com/user-attachments/assets/f6f0f8d7-0ca7-46ec-a352-4fdca726c3f7" />


# Variável Alvo

**Classificação:** A coluna `Exited` será a variável alvo para os modelos de classificação, indicando se um cliente deixou o banco (1) ou não (0).

**Regressão:** A coluna `CreditScore` foi escolhida como variável alvo para os modelos de regressão.

# **Conclusão**

## **Regressão**

**Melhor desempenho:** O modelo de Regressão Linear foi o melhor para a previsão do `CreditScore`, pois apresentou o menor RMSE (96.88). Isso significa que, em média, o erro das previsões do algoritmo foi de aproximadamente 97 pontos. O fato de a Regressão Linear ser mais indicada para dados que se apresentam de forma linear foi o motivo de seu resultado superior aos demais algoritmos, mesmo que os outros sejam mais complexos.

**Pior Desempenho:** A Árvore de Regressão teve um desempenho muito ruim, com um erro médio de 141 pontos. Isso é esperado, pois árvores de decisão únicas tendem a ser instáveis e a cometer mais erros do que modelos mais robustos como o Random Forest.

**Gráfico de Distribuição de Erros:** O gráfico foi usado para apresentar de forma visual os resultados de todos os quatro algoritmos. Percebe-se que, quanto mais "pontudo" o gráfico, melhor o resultado, enquanto linhas mais "espalhadas" indicam um desempenho pior. É o caso da linha azul (Regressão Linear) e da linha laranja (Árvore de Regressão), respectivamente.

## **Classificação**

**Melhor Resultado:** O Random Forest e o SVM foram os melhores modelos quando avaliada a acurácia, ambos com 86%. A diferença entre eles é que o Random Forest se destaca ligeiramente com o maior F1-Score (0.76) e um bom Recall (0.73), apresentando um equilíbrio: acerta bastante quem vai sair, sem classificar muitos clientes fiéis de forma errada. Já o SVM tem um pouco mais de precisão (85%), mas seu Recall mais baixo (0.70) indica que ele "deixa passar" mais clientes que realmente saem do que o Random Forest.

**Pior resultado:** A Regressão Logística teve o pior desempenho geral, com um F1-Score de 0.61. Seu principal problema é a baixa capacidade de identificar os clientes que de fato saíram.

# **Defesa dos Hiperparâmetros**

**Regressão Logística (`LogisticRegression(max_iter=200)`):** O padrão é `max_iter=100`. Aumentar o número máximo de iterações para 200 é uma prática comum para garantir que o otimizador do modelo tenha tempo necessário para encontrar uma solução, assegurando a estabilidade do treinamento.

**Árvore de Decisão (`DecisionTreeClassifier(random_state=42)`):** Foram utilizados os parâmetros padrão para avaliar o desempenho base do modelo. O `random_state=42` garante a reprodutibilidade dos resultados.

**Random Forest (`RandomForestClassifier(n_estimators=100, random_state=42)`):** A escolha segue os valores padrão da biblioteca, que são um ponto de partida robusto e amplamente utilizado na comunidade.

**SVM (`SVC(kernel='rbf')`):** Foi utilizado o valor padrão. O kernel `rbf` (Radial Basis Function) é extremamente versátil e poderoso, capaz de encontrar relações não lineares complexas, sendo a escolha inicial na maioria dos problemas de classificação.

**K-NN (`KNeighborsClassifier(n_neighbors=5)`):** O valor `n_neighbors=5` é o padrão do Scikit-learn. É uma escolha balanceada que considera uma vizinhança local para a classificação, sem ser excessivamente sensível a ruídos (como seria com k=1) ou excessivamente generalista.
