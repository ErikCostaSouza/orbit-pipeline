Este projeto, GeoDataFlow, é uma plataforma de engenharia de dados (Downstream) projetada para processar dados de Observação da Terra (EO) em escala. Ele resolve o desafio de transformar terabytes de imagens brutas de satélite em informações prontas para consumo por modelos de Machine Learning e BI.

A arquitetura segue o padrão de Data Lakehouse e foca em três pilares principais:

Ingestão Padronizada: Uso de catálogos STAC para busca eficiente de ativos espaciais sem necessidade de download massivo.

Processamento Distribuído (Batch): Pipeline que automatiza o cálculo de índices biofísicos (ex: NDVI) e normalização de dados multiespectrais.

Armazenamento de Alta Performance: Implementação do padrão COG (Cloud Optimized GeoTIFF), permitindo que os dados sejam lidos de forma parcial e eficiente via nuvem.

🎯 Objetivo
Demonstrar uma infraestrutura de dados moderna capaz de servir como base para monitoramento ambiental, análise de safras agrícolas e inteligência de mercado.
