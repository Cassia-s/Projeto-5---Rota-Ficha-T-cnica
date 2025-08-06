# Projeto-5-Rota-Ficha-Técnica
## Construção de um Data Warehouse para Análise de Vendas da Superstore

  </details>
  
  <details>
  <summary><strong style="font-size: 16px;">Resumo executivo</strong></summary>
    
Este projeto teve como objetivo principal a transformação de dados brutos e desestruturados, provenientes de múltiplas fontes, em um modelo de dados analítico e robusto. Através do processo de ETL (Extração, Transformação e Carga), foi construído um Data Warehouse no Google BigQuery, utilizando a modelagem dimensional Star Schema. A solução permite que a empresa Superstore realize análises de vendas mais eficientes e estratégicas, cruzando informações de clientes, produtos, localização, pedidos e concorrentes de forma integrada.

  </details>
  
  <details>
  <summary><strong style="font-size: 16px;">Problema de negócio</strong></summary>
    
Os dados de vendas da Superstore, originalmente em um arquivo CSV, e as informações de concorrentes, obtidas via web scraping, encontravam-se isolados e sem uma estrutura relacional otimizada. A ausência de um sistema tabular unificado e uma arquitetura de dados consistente dificultava a realização de consultas complexas, a medição de KPIs (Key Performance Indicators) e a extração de insights valiosos para a tomada de decisões.

  </details>
  
  <details>
  <summary><strong style="font-size: 16px;">Ferramentos utilizadas</strong></summary>
    
 •	BigQuery: criação das tabelas, execução das consultas SQL, transformação e modelagem dimensional.
 
 •	Python (pandas + bigquery): leitura, limpeza e carga dos dados automatizada.
 
 •	Google Sheets (IMPORTHTML): extração de dados externos via scraping.
 
 •	Apresentação google: criação da apresentação final com storytelling visual.
 

  </details>
  
  <details>
  <summary><strong style="font-size: 16px;">Equipe</strong></summary>
    
Cassia Silva

  </details>
  
  <details>
  <summary><strong style="font-size: 16px;">Solução técnica</strong></summary>
    
A solução implementada foi a criação de um Data Warehouse utilizando a modelagem Star Schema. Esta arquitetura foi escolhida por sua capacidade de otimizar consultas analíticas, facilitar a compreensão dos dados e simplificar a agregação de métricas.

•	Modelo de dados:

o	Tabela de fatos (fact_sales): Tabela central que armazena as métricas quantitativas de cada transação de venda, como sales, profit, quantity e shipping_cost. Possui chaves estrangeiras (FKs) que se conectam às tabelas de dimensão.

o	Tabelas de dimensão (dim_...): Tabelas que fornecem o contexto descritivo para os fatos. Cada dimensão armazena atributos sobre:

- dim_customer (Quem comprou?): customer_id, customer_name, segment.

- dim_product (O que foi vendido?): product_id, product_name, category, sub_category.

- dim_location (Onde aconteceu?): location_id, city, state, country, region.

- dim_order (Quando aconteceu?): order_id, order_date, ship_date, order_priority, ship_mode.

- dim_concorrentes (Dados contextuais): concorrente_id, company, country, industry.

  </details>
  
  <details>
  <summary><strong style="font-size: 16px;">Processo de ETL pipeline de dados</strong></summary>
    
Um pipeline de ETL automatizado foi desenvolvido para extrair os dados, transformá-los e carregá-los no BigQuery, seguindo uma ordem de dependência lógica.
•	Tecnologias:
o	Linguagem de programação: Python
o	Bibliotecas: Pandas para manipulação e transformação de dados, pandas-gbq e google-cloud-bigquery para a carga de dados no BigQuery.
o	Destino: Google BigQuery.
•	Fluxo de trabalho do pipeline:
1.	Extração: Dados brutos são lidos do arquivo CSV da Superstore e de uma fonte externa (web scraping de dados de concorrentes).
2.	Transformação: Os dados são limpos, padronizados e agregados. Chaves primárias (surrogate keys) são geradas para cada tabela de dimensão. A tabela de fatos é construída em seguida, utilizando as chaves estrangeiras para referenciar as dimensões já criadas.
3.	Carga: Os DataFrames processados são carregados na ordem correta para o BigQuery:
	Primeiro, todas as tabelas de dimensão.
	Por último, a tabela de fatos, que depende das chaves das dimensões.

  </details>
  
  <details>
  <summary><strong style="font-size: 16px;">Entregas e resultados</strong></summary>
    
•	Código: Um script Python (rota_etl_superstore.py ou .ipynb) contendo a lógica completa de ETL.
•	Estrutura de dados: Um conjunto de tabelas de fatos e dimensões no Google BigQuery.
•	Documentação:
o	Diagrama de modelagem Star Schema.
o	Fluxograma do pipeline de atualização de dados.
•	Análise de Desempenho: A nova estrutura permite consultas complexas com maior eficiência e menor custo computacional, proporcionando uma base sólida para a análise de BI.

  </details>
  
  <details>
  <summary><strong style="font-size: 16px;">Recomendações futuras</strong></summary>
    
•	Automatizar o pipeline - Agendar o pipeline de ETL para execução automática e contínua.
•	Implementar (SCD) Rastrear mudanças nos dados (ex: cliente mudando de segmento) para análises históricas precisas.
•	Ampliar a base com novas fontes (e-commerce, SAC, redes sociais)
•	Criar visões agregadas e dashboards para acompanhamento de KPIs

  </details>
  
  <details>
  <summary><strong style="font-size: 16px;">Conclusão</strong></summary>

Este projeto consolidou o uso de boas práticas de engenharia de dados com foco em análise de negócios, e mostrou como transformar um arquivo bruto em uma estrutura analítica escalável. A modelagem com Star Schema, combinada ao processo ETL limpo e bem documentado, permitiu a construção de uma base sólida para decisões baseadas em dados.

  </details>
  
  <details>
  <summary><strong style="font-size: 16px;">Links</strong></summary>
    
•	[Apresentações google](https://docs.google.com/presentation/d/1sGMw_1xxm-tVbcfihM8Qujl1IWJSM1VAc0pAmAUibgs/edit?usp=sharing)
•	[Apresentação de vídeo (Loom) 
