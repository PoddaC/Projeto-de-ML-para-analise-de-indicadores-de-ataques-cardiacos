# Projeto-de-ML-para-analise-de-indicadores-de-ataques-cardiacos
Ánalise em cima do dataset ''Indicators of Heart Disease''.

## Objetivo
Comparar três modelos de classificação (Regressão Logística, Random Forest 
e Árvore de Decisão) na previsão de ataque cardíaco a partir de 
indicadores de saúde auto-reportados.

## Dataset
- **Fonte**: Personal Key Indicators of Heart Disease (Kaggle)
- **Origem**: BRFSS 2022 - Behavioral Risk Factor Surveillance System (CDC)
- **Tamanho**: ~445 mil registros, 40 variáveis
- **Target**: HadHeartAttack (Yes/No) — fortemente desbalanceada (5,6% positivos)

## Metodologia
1. Tratamento de nulos (mediana/moda)
2. One-hot encoding das categóricas
3. Balanceamento via `class_weight='balanced'`
4. Seleção de top 20 features pelos coeficientes
5. Comparação por AUC-ROC

## Resultados

| Modelo | AUC | Recall (1) | Precision (1) |
|--------|-----|------------|---------------|
| Regressão Logística | **0.879** | 0.77 | 0.22 |
| Random Forest | 0.861 | 0.75 | 0.20 |
| Árvore de Decisão | 0.835 | — | — |

**Modelo final**: Regressão Logística — o sinal nos dados é predominantemente 
linear, sem ganhos com modelos mais complexos.

## Principais fatores de risco identificados
Angina prévia, idade avançada, AVC anterior, saúde geral ruim, 
sexo masculino, diabetes — todos consistentes com a literatura médica.

## Como executar
1. Abra o notebook `Hearth_disease_ML.ipynb` no Google Colab
2. Execute todas as células (Ctrl+F9)
3. O dataset é baixado automaticamente via `kagglehub`

## Tecnologias
Python, pandas, scikit-learn, matplotlib, seaborn, kagglehub

## Limitações
- Dados auto-reportados (viés de memória)
- Modelo de triagem, não substitui avaliação médica
- Alto número de falsos positivos (precision baixa)
