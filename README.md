Título: Projeto de Big Data — Consórcio Predict 📊📈

Problema: O projeto visa resolver a falta de visão territorial do mercado de consórcios no Brasil. O objetivo é identificar regiões com maior potencial de crescimento e projetar o cenário de cotas ativas para 2026, apoiando a tomada de decisão comercial e o planejamento tático do negócio.

Dados:
- origem: Extraídos via API e de Fontes Públicas Oficiais.
- descrição: Conjunto de dados estruturados contendo indicadores macroeconômicos (PIB total, PIB per capita, IPCA mensal), demográficos (população residente), tendências de busca (Google Trends para consórcios) e métricas do setor (cotas ativas totais e de imóveis). A variável alvo principal é de estoque: `Quantidade_total_cotas_ativas`.

Tecnologias:
- Python (Pandas, Prophet para previsões)
- Databricks (Data LakeHouse para armazenamento e processamento)
- SQL
- Power BI (Dashboards e relatórios)
- Flask (Microsserviço de API nativo com CORS)

Metodologias:
- CRISP-DM
- KDD
- Scrum / Kanban
- DataOps

Pipeline: Coleta (APIs) → Limpeza (Padronização e exclusão de incompletos) → Transformação (Agregação trimestral por UF e Operação) → Análise (Modelagem preditiva e descritiva) → Visualização (Dashboard e Endpoints)

Resultados: O modelo preditivo desenvolvido alcançou 98,06% de acurácia global (MAPE de 1,94%) na base de teste. O pipeline automatizado treinou e serializou em JSON 27 modelos independentes para os estados brasileiros e centenas de variações de cruzamentos por Administradora e Segmento.

Insights: A análise revelou que focar na tendência estrutural de crescimento linear por partes (identificando acelerações ou desacelerações do mercado) é mais efetivo do que tentar capturar sazonalidades de curto prazo. Isso viabiliza traçar cenários base, otimistas e pessimistas com precisão, permitindo criar rankings de administradoras e acompanhar o market share regional de forma granular.

Como executar: 
1. Faça o clone do repositório e instale as dependências listadas no projeto.
2. Execute o script automatizado em lote (*batch*) para treinar e exportar os arquivos `.json` dos modelos Prophet.
3. Inicie o microsserviço executando o servidor Flask.
4. Realize inferências consumindo as rotas (ex: `GET /api/prever/<estado_ou_global>/<meses>`) através de aplicações frontend ou dashboard.