# Trilha A: Dados & IA

O objetivo desta trilha é construir um pipeline inteligente para coletar e análise de dados de precificação multicloud, propondo modelos de IA para prever custo e fornecer insumos estratégicos para gestão financeira em ambientes multicloud.


## Estrutura da solução

### Componentes principais
- **Fonte de Dados:** AWS Pricing API, Azure Calculator API.
- **Pipeline ETL:** 
    - Extração dos dados via API.
    - Processamento e limpeza.
    - Armazenamento em um banco de dados, neste caso, um arquivo `.csv`.
- **Análise dos dados:**
    - Visualização dos dados.
    - Modelos de IA para prever custo.
    - Clustering para agrupar padrões de consumo.
