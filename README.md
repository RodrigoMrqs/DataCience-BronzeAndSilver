# Projeto: Pipeline Medalion — Bronze & Silver (Cibersegurança)

## Pré-requisitos
- Python 3.9+
- Bibliotecas: pandas, numpy, matplotlib, seaborn, pyarrow

## Instalação
```
pip install pandas numpy matplotlib seaborn pyarrow
```

## Estrutura de Arquivos
```
data/
├── incidents_master.csv           # Dataset bruto original
├── bronze/
│   ├── bronze.parquet             # Camada Bronze
│   ├── metadata_bronze.json       # Metadados de ingestão
│   └── relatorio_qualidade_bronze.csv
└── silver/
    ├── silver.parquet             # Camada Silver (pronta para ML)
    ├── documentacao_transformacoes.csv
    ├── checklist_anti_leakage.csv
    ├── grafico_1_vetores_impacto.png
    ├── grafico_2_evolucao_temporal.png
    ├── grafico_3_janelas_temporais.png
    └── grafico_4_paises_vs_vetores.png
```

## Como Executar
1. Coloque `incidents_master.csv` na pasta `data/`
2. Abra e execute o notebook `notebook.ipynb` célula por célula, em ordem
3. Os arquivos de saída serão gerados automaticamente nas pastas bronze/ e silver/

## Label para ML
- `is_high_impact = 1` se: registros comprometidos > 100.000 OU downtime > 72h
- `is_high_impact = 0` caso contrário
- Distribuição: 371 positivos (43,6%) / 479 negativos (56,4%)

## Colunas Removidas (Anti-Leakage)
quality_score | quality_grade | confidence_tier | review_flag