# projeto-inadimplencia2
🧠 Previsão de Inadimplência com Técnicas Supervisionadas

Este projeto tem como objetivo aplicar modelos de Machine Learning supervisionados para prever a inadimplência de clientes de uma instituição de crédito, utilizando informações financeiras e comportamentais. O estudo compara duas abordagens — Regressão Logística e Árvore de Decisão — e busca apoiar a tomada de decisões mais assertivas na concessão de crédito.

📂 Sobre o Dataset

Origem: Base hipotética construída para fins de análise.

Formato: CSV delimitado por ponto e vírgula (;).

Registros: 10.986 clientes.

Variável-alvo: Resposta (0 = adimplente, 1 = inadimplente).

🧾 Variáveis disponíveis
Coluna	Descrição
cliente	Identificador único do cliente (não usado na modelagem)
Resposta	Status de pagamento do cliente (0 = adimplente, 1 = inadimplente)
RegRisc	Região de risco (I, II, III, IV)
Atrasos	Número de dias de atraso nos pagamentos
TempoRel	Tempo de relacionamento com a instituição (em dias)
valorFatura	Valor médio da fatura mensal
GastosAlim	Percentual de gastos com alimentação
RendaMensal	Renda mensal do cliente
🧩 Hipóteses levantadas

Clientes com maior número de atrasos têm maior chance de inadimplência ✅

Regiões de risco mais altas (III e IV) estão associadas a maior inadimplência ❌

Menor tempo de relacionamento indica maior risco de inadimplência ✅

Existe correlação entre valor da fatura e renda mensal ❌

Gastos com alimentação indicam menor capacidade de pagamento ❌

⚙️ Etapas Realizadas
1. 📊 Análise Exploratória de Dados (EDA)

Verificação de tipos de dados e ausência de valores nulos.

Histogramas e boxplots para explorar distribuição e identificar outliers.

Estatísticas descritivas (média, desvio padrão, quartis).

Matriz de correlação entre variáveis numéricas.

Comparações entre adimplentes vs inadimplentes.

2. 🧼 Pré-Processamento

Conversão da variável cliente para string (tratada apenas como ID).

Codificação da variável RegRisc em dummies (II, III, IV).

Tratamento de outliers em valorFatura (cap em R$ 10.000).

Padronização dos atributos numéricos com StandardScaler.

Separação em treino (80%) e teste (20%) com estratificação por classe.

3. 🤖 Modelagem e Avaliação

Baseline: DummyClassifier (classe mais frequente, ~50% de acurácia).

Modelos candidatos:

Regressão Logística (linear, interpretável).

Árvore de Decisão (não linear, interpretável via regras).

Validação cruzada com StratifiedKFold (5 folds).

Otimização de hiperparâmetros com RandomizedSearchCV.

Métricas utilizadas: Acurácia, Precisão, Recall, F1-score, ROC AUC.

Análise de erros com matriz de confusão.

🧪 Ferramentas e Bibliotecas

Python (pandas, numpy)

Visualização: seaborn, matplotlib

Modelagem: scikit-learn

📉 Principais Insights

Atrasos: Melhor preditor de inadimplência (correlação ≈ 0.38).

Tempo de Relacionamento: Clientes mais antigos tendem a ser mais confiáveis.

Regiões de Risco: Contraintuitivamente, I e II concentraram mais inadimplentes.

Gastos com Alimentação: Clientes que gastam mais nessa categoria tendem a ser mais adimplentes.

Árvore de Decisão: Melhor desempenho (acurácia ~98%), mas precisa de validação em novos dados para evitar overfitting.

📁 Organização dos Arquivos
Arquivo	Descrição
Inadimplencia_quantitativa_2.csv	Base de dados original.
Template_MVP_ML_&_Analytics_Filled.ipynb	Notebook principal seguindo a estrutura do template MVP.
TecnicaSupervisionadaClassificacao_Inadimplencia.ipynb	Notebook independente do projeto.
README.md	Descrição geral do projeto.
📌 Conclusão

Este estudo mostrou que a previsão de inadimplência pode ser realizada com alta acurácia utilizando modelos supervisionados. A Árvore de Decisão apresentou melhor desempenho, mas recomenda-se validação em dados futuros e o uso de modelos de ensemble (Random Forest, XGBoost) para maior robustez.

Próximos passos incluem:


Testes com algoritmos mais sofisticados.

Implementação em produção com monitoramento contínuo de performance e drift.
