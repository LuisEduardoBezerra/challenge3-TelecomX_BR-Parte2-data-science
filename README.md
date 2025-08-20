# Análise e Previsão de Evasão de Clientes - TelecomX BR
📝 Resumo do Projeto
Este projeto de ciência de dados tem como objetivo principal analisar os fatores que levam os clientes da TelecomX BR a cancelar seus serviços (evasão ou churn) e construir modelos preditivos para identificar os clientes com maior probabilidade de evadir. O projeto segue um fluxo de trabalho completo, desde a extração e transformação dos dados até a modelagem e a proposição de estratégias de negócios.

🚀 Metodologia
O desenvolvimento do projeto foi dividido nas seguintes etapas:

1. Extração e Carregamento de Dados
Os dados foram extraídos de um arquivo .json hospedado em um repositório no GitHub.

A função pd.json_normalize foi utilizada para transformar a estrutura aninhada do JSON em um DataFrame plano, facilitando a manipulação.

2. Pré-processamento e Limpeza
Tratamento de Dados Ausentes: A coluna account.Charges.Total, que estava em formato de texto e continha espaços em branco, foi convertida para tipo numérico após a substituição dos valores ausentes (' ') por NaN e sua posterior remoção.

Renomeação de Colunas: As colunas foram renomeadas para o português, tornando o conjunto de dados mais intuitivo.

Conversão de Variáveis Categóricas: As variáveis categóricas foram transformadas em formato numérico utilizando One-Hot Encoding (pd.get_dummies), uma etapa essencial para a compatibilidade com a maioria dos algoritmos de machine learning.

Divisão Treino/Teste: O conjunto de dados foi dividido em 80% para treino e 20% para teste, com estratificação para garantir que a proporção de clientes que evadiram fosse mantida em ambos os conjuntos.

3. Análise Exploratória de Dados (EDA)
Taxa de Evasão: A taxa de evasão geral da empresa foi identificada em aproximadamente 26.5%, indicando um problema significativo.

Análise Demográfica: Clientes sem parceiro e/ou sem dependentes apresentaram uma tendência maior a evadir.

Análise de Variáveis Numéricas: A análise visual por meio de boxplots e gráficos de dispersão revelou que o tempo de serviço (TempoServico) e o custo total (CustoTotal) são os fatores mais críticos. A maioria dos clientes que evadem são novos, com pouco tempo de serviço e baixo custo total.

4. Modelagem e Avaliação
Foram construídos dois modelos de classificação para prever a evasão, e seus desempenhos foram avaliados com base em métricas como Acurácia, Precisão, Recall, F1-score e a Matriz de Confusão.

Modelo	Acurácia	Precisão	Recall	F1-Score
Regressão Logística	88.10%	65.58%	52.94%	58.58%
Random Forest	87.92%	64.66%	48.93%	55.71%

Exportar para as Planilhas

💡 Resultados e Conclusão
Com base na avaliação, o modelo de Regressão Logística teve um desempenho superior neste caso específico. Embora a acurácia de ambos os modelos seja similar, a Regressão Logística superou o Random Forest nas métricas mais importantes para este problema: Precisão e Recall.

A principal vantagem da Regressão Logística foi sua maior capacidade em capturar corretamente os clientes que iriam evadir (recall mais alto), resultando em um menor número de falsos negativos. Para a equipe de negócios, isso significa menos oportunidades de intervenção perdidas.

Com base nos dados e nos modelos, as seguintes estratégias de retenção são propostas:

* Foco em Clientes Novos: Priorize a atenção e o suporte a clientes nos primeiros meses de serviço, período de maior risco de evasão. Um programa de onboarding robusto e proativo é crucial.
* Incentivo à Fidelização: Crie programas de incentivo ou ofereça descontos atrativos para clientes que optarem por contratos de maior duração (anuais ou de dois anos).
* Ações Proativas com o Modelo Preditivo: Implemente o modelo de Regressão Logística para identificar clientes em risco de evasão em tempo real. A equipe de retenção pode então intervir com ofertas personalizadas, suporte adicional ou benefícios especiais para evitar o cancelamento.
