🛰️ GeoDataFlow: Detecção de Mudanças e Vigilância ESG
O GeoDataFlow é uma pipeline de engenharia de dados (Downstream) projetada para o monitoramento automatizado de áreas protegidas. O projeto utiliza dados de observação da Terra para identificar mudanças na cobertura do solo, como desmatamento ou construções ilegais, através de análise temporal.

🎯 O Problema
Órgãos de fiscalização e empresas com metas ESG enfrentam o desafio de monitorar áreas massivas em intervalos curtos. O processamento manual de imagens de satélite é lento, caro e difícil de escalar.

Esta pipeline automatiza a detecção de anomalias, transformando "pixels brutos" em "alertas de infração".

⚙️ Arquitetura da Solução
A pipeline foi construída seguindo os princípios de um Data Lakehouse Espacial:

Ingestion (Bronze): Busca automatizada de imagens multiespectrais do satélite Sentinel-2 via API STAC (Microsoft Planetary Computer).

Processing (Silver): * Cálculo de índices de vegetação (NDVI) para diferentes janelas temporais.

Aplicação de algoritmos de Change Detection para isolar variações na biomassa.

Filtragem de ruído (nuvens e variações sazonais).

Serving (Gold): Geração de máscaras de mudança em formato COG (Cloud Optimized GeoTIFF) e relatórios JSON com as coordenadas e área (hectares) da alteração detectada.

🛠️ Stack Tecnológica
Orquestração: [Defina aqui, ex: Prefect ou Airflow]

Linguagem: Python 3.10+

Bibliotecas de EO: pystac-client, rasterio, stackstac, geopandas

Processamento: NumPy e Xarray

Armazenamento: Local / S3 (Parquet e COG)

📊 Exemplo de Output
Ao comparar duas datas (T1 e T2), a pipeline gera uma camada de evidência:

Input: Duas imagens brutas de 500MB.

Output: Um arquivo JSON de 2KB contendo a prova da mudança:

JSON

{
  "alerta_id": "ESG-2024-001",
  "coordenadas": [-54.32, -12.45],
  "area_degradada_ha": 15.4,
  "confianca": 0.92,
  "timestamp": "2024-10-27T..."
}
