# 📉 Previsão de Cancelamento de Clientes (Churn)

Pipeline completo de Machine Learning feito com **Python, pandas e scikit-learn** para prever quais clientes de uma empresa de telecom têm mais chance de cancelar o serviço.

[![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/kauesalazarcardoso/previsao-churn/blob/main/previsao_churn.ipynb)

---

## 🎯 O problema

*Churn* é quando o cliente cancela e vai embora. Conquistar um cliente novo custa bem mais do que manter um antigo, então saber **antes** quem pode sair ajuda a empresa a agir a tempo, por exemplo com um desconto ou um atendimento melhor.

**Quem se beneficia:**
- a equipe de retenção, que sabe em quem focar;
- o marketing, que acerta o público das campanhas;
- a gestão, que perde menos receita;
- o próprio cliente, que recebe ajuda antes de ficar insatisfeito.

É um problema de **Classificação**, porque a resposta é "cancela" ou "não cancela".

## 📊 Dataset

**Telco Customer Churn** (IBM, também disponível no [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)): cerca de 7 mil clientes e 21 colunas. O notebook baixa os dados sozinho, então não é preciso fazer download manual.

## 🔧 O que o notebook faz

1. **Carrega** os dados com pandas.
2. **Análise exploratória**, com gráficos de churn por contrato, tempo de casa e mensalidade.
3. **Tratamento**: converte `TotalCharges` para número, **elimina valores ausentes** (11 linhas), **remove duplicadas** (22 linhas), **padroniza** as colunas numéricas (`StandardScaler`) e transforma as categóricas em números (`OneHotEncoder`).
4. **Divide** em treino e teste (80/20, estratificado).
5. **Treina dois algoritmos**: Regressão Logística e Random Forest.
6. **Avalia** com acurácia, precisão, recall, F1, ROC AUC e matriz de confusão.
7. Mostra as **características que mais pesam** no cancelamento.

## 📈 Resultados (conjunto de teste)

| Modelo | Acurácia | Precisão | Recall | F1 | ROC AUC |
|---|---|---|---|---|---|
| Regressão Logística | 0,744 | 0,511 | 0,776 | 0,616 | 0,846 |
| Random Forest | 0,766 | 0,544 | 0,722 | 0,620 | 0,843 |

*(números obtidos no Google Colab; podem variar bem pouco em outras versões das bibliotecas)*

Os dois modelos encontram **cerca de 3 em cada 4 clientes que vão cancelar**. O Random Forest ficou um pouco melhor no geral (acurácia, precisão e F1), enquanto a Regressão Logística encontrou um pouco mais de clientes que iam cancelar (recall). Os fatores que mais pesam no cancelamento são o **contrato mês a mês**, o **pouco tempo de casa** e os **valores cobrados**.

## ▶️ Como executar

### Opção 1: Google Colab (mais fácil)
1. Abra o `previsao_churn.ipynb` no [Google Colab](https://colab.research.google.com/) (menu **Arquivo → Fazer upload de notebook**) ou clique no botão "Abrir no Colab" lá em cima.
2. Clique em **Ambiente de execução → Executar tudo**.

As bibliotecas já vêm instaladas no Colab.

### Opção 2: No seu computador
```bash
git clone https://github.com/kauesalazarcardoso/previsao-churn.git
cd previsao-churn
pip install -r requirements.txt
jupyter notebook previsao_churn.ipynb
```

## 👤 Autor

**Kauê Salazar Cardoso**
Análise e Desenvolvimento de Sistemas – IFRS Campus Rolante
