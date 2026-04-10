# Projeto: Pipeline Medalion — Bronze & Silver (Cibersegurança)

### Este repositório contém a implementação de um pipeline de dados voltado para cibersegurança, seguindo a arquitetura de medalhão. O foco principal é a transformação de dados brutos em um dataset de alta qualidade e pronto para modelos de Machine Learning, garantindo a integridade e a governança dos dados.

# 📌 Objetivo do Projeto
O objetivo deste projeto é construir um fluxo rastreável de ingestão e tratamento de dados. Partindo de arquivos brutos de incidentes e dados financeiros, o pipeline realiza a padronização, auditoria de qualidade e limpeza profunda, culminando em uma camada analítica (Prata) livre de inconsistências e vazamento de dados (data leakage).

# 🏗️ Estrutura do Repositório
De acordo com a organização do projeto entregue:

├──📂 DataCience-BronzeAndSilver/

│   ├── 📂data/

   ---     └──📂 raw/   : Arquivos originais (CSV/JSON)

   ---    └──📂bronze/  : Dados em Parquet com metadados de ingestão

   ---     └──📂silver/  : Dados limpos e prontos para Machine Learning

│   ├── 📂notebooks/   : Pipeline principal e Análise Exploratória

│   ├── 📂reports/  : Relatórios de qualidade e Checklist Anti-Leakage

│   └── 📄.git/  : Versionamento do código

# 🛠️ Etapas do Pipeline de Dados
## 1. Camada Bronze (Ingestão e Metadados)
Nesta fase, os arquivos de origem são lidos e convertidos para o formato Parquet para otimizar o armazenamento e a performance.

Padronização: Ajuste de nomes de colunas e tipos básicos.

Governança: Inclusão de metadados técnicos:

Nome do arquivo original.

Timestamp da carga.

Quantidade de registros.

Hash de integridade (SHA-256).

## 2. Validação de Qualidade
Antes da promoção para a camada Prata, os dados da Bronze são submetidos a regras automáticas de validação:

Verificação de valores nulos e duplicatas.

Identificação de categorias inconsistentes.

Formatação de campos de data fora do padrão.

## 3. Camada Prata (Transformação e Feature Engineering)
Nesta camada, os dados são refinados para uso analítico:

Limpeza: Tratamento de valores ausentes e remoção de ruídos.

Feature Engineering: Criação do rótulo final (label) para predição.

Segurança de Dados: Remoção de colunas com risco de data leakage (variáveis que revelam o resultado antes da predição).

# 📊 Análise Exploratória (EDA)
O projeto inclui visualizações gráficas essenciais para compreensão do dataset:

Distribuição de Incidentes: Frequência por tipo de ataque.

Impacto Financeiro: Correlação entre incidentes e perdas financeiras.

Tendência Temporal: Volume de ataques ao longo do tempo.

### ## Checklist Anti-Leakage

### +------------------+----------+------------------------------------------------+


### |            Variável         | Status   | Justificativa                       |


### +------------------+----------+------------------------------------------------+


### | outcome_status   | Removido | Variável de resposta (vazamento de dados).     |


### | future_costs     | Removido | Valor gerado após o incidente.                 |


### | incident_id      | Mantido  | Necessário para rastreabilidade.               |


### | timestamp        | Mantido  | Convertido para formato padrão.                |


### +------------------+----------+------------------------------------------------+


## 🔗 Data Lineage (Linhagem de Dados)

### O fluxo de dados segue a trilha:
### Origem (Raw) ➔ Conversão & Metadados (Bronze) ➔ Regras de Qualidade ➔ Transformação & Limpeza (Prata) ➔ Dataset Final (ML Ready).

## 🚀 Como Executar o Projeto

### Clone o respositório.

### Instale as dependências: pip install pandas pyarrow fastparquet matplotlib seaborn.

### Execute o notebook na pasta notebooks/ para processar as camadas.

### Os arquivos finais estarão disponíveis em data/silver/ no formato Parquet.
