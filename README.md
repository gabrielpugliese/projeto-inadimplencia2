# projeto-inadimplencia2
MVP Sprint: Machine Learning & Analytics

# 🧠 Previsão de Inadimplência com Técnicas Supervisionadas

Este projeto tem como objetivo aplicar **modelos de Machine Learning supervisionados** para prever a inadimplência de clientes de uma instituição de crédito, utilizando informações financeiras e comportamentais. Foram comparadas duas abordagens — **Regressão Logística** e **Árvore de Decisão** — para apoiar a **tomada de decisões mais assertivas** na concessão de crédito.

---

## 📂 Sobre o Dataset

- **Origem**: Base hipotética.
- **Formato**: CSV delimitado por ponto e vírgula (`;`)
- **Registros**: 10.986 clientes
- **Variável-alvo**: `Resposta` (0 = adimplente, 1 = inadimplente)

### 🧾 Variáveis disponíveis

| Coluna         | Descrição |
|----------------|-----------|
| `cliente`      | Identificador único do cliente |
| `Resposta`     | Status de pagamento do cliente |
| `RegRisc`      | Região de risco (I, II, III, IV) |
| `Atrasos`      | Número de dias de atraso nos pagamentos |
| `TempoRel`     | Tempo de relacionamento com a instituição (em dias) |
| `valorFatura`  | Valor médio da fatura mensal |
| `GastosAlim`   | Percentual de gastos com alimentação |
| `RendaMensal`  | Renda mensal do cliente |

---

## 🧩 Hipóteses levantadas

1. Clientes com maior número de atrasos têm maior chance de inadimplência ✅  
2. Regiões de risco mais altas (III e IV) estão associadas a maior inadimplência ❌  
3. Menor tempo de relacionamento indica maior risco de inadimplência ✅  
4. Existe correlação entre valor da fatura e renda mensal ❌  
5. Gastos com alimentação indicam menor capacidade de pagamento ❌  

---

## ⚙️ Etapas Realizadas

### 1. 📊 Análise Exploratória de Dados (EDA)
- Verificação de tipos de dados e dados ausentes
- Histogramas e boxplots para entender distribuição e outliers
- Estatísticas descritivas (média, desvio padrão)
- Matriz de correlação
- Comparações entre grupos (adimplentes vs inadimplentes)

### 2. 🧼 Pré-Processamento
- Conversão da variável `cliente` para string
- Codificação da variável `RegRisc` com **One-Hot Encoding**
- Tratamento de outliers em `valorFatura` (cap em R$ 10.000)
- Padronização com `StandardScaler`
- Separação em conjunto de treino e teste com `train_test_split`

### 3. 🤖 Modelagem
- **Baseline**: DummyClassifier
- **Modelos candidatos**: Regressão Logística e Árvore de Decisão
- **Validação cruzada** com StratifiedKFold
- **Otimização de hiperparâmetros** com RandomizedSearchCV
- Avaliação com métricas: Acurácia, Precisão, Recall, F1-score e ROC AUC
- Análise de erros via matriz de confusão

---

## 🧪 Ferramentas e Bibliotecas

- Python (`pandas`, `numpy`)
- Visualização: `seaborn`, `matplotlib`
- Modelagem: `scikit-learn`

---

## 📉 Principais Insights

- **Atrasos**: Boa preditora de inadimplência (correlação ≈ 0.38)  
- **Tempo de relacionamento**: Clientes com histórico mais longo tendem a ser mais confiáveis  
- **Regiões de Risco**: Contraintuitivamente, regiões I e II concentraram mais inadimplentes  
- **Gastos com alimentação**: Maior percentual de gastos se correlaciona com **maior** capacidade de pagamento  
- **Árvore de Decisão**: Melhor desempenho (acurácia ~98%), mas precisa de validação em dados futuros para evitar overfitting  

---

## 📁 Organização dos Arquivos

| Arquivo | Descrição |
|---------|-----------|
| `Inadimplencia_quantitativa_2.csv` | Base de dados original |
| `MVP_Gabriel_Pugliese.ipynb` | Notebook com toda a análise |
| `README.md` | Descrição geral do projeto |

---

## 📌 Conclusão

Este estudo mostrou que a previsão de inadimplência pode ser realizada com **alta acurácia** utilizando técnicas supervisionadas.  
A **Árvore de Decisão** se destacou como melhor modelo, mas recomenda-se validação temporal, adição de novas variáveis e uso de ensembles (Random Forest, XGBoost) para maior robustez e generalização.  

