# Apache Spark (PySpark)

O **Apache Spark** é um motor de processamento de dados unificado, projetado para ser rápido e lidar com grandes volumes de informações (Big Data) de forma distribuída. O **PySpark** é a biblioteca que permite utilizar o Spark através da linguagem Python.

## Por que utilizar o PySpark?
Diferente do Python tradicional (como o Pandas), que processa dados na memória de apenas uma máquina, o PySpark distribui o trabalho entre vários nós de um cluster, permitindo processar Petabytes de dados com eficiência.



[Image of Apache Spark architecture overview]


## Principais Componentes do ecossistema Spark:
* **Spark SQL:** Permite executar consultas estruturadas usando SQL ou a API de DataFrames.
* **Spark Streaming:** Processamento de dados em tempo real.
* **MLlib:** Biblioteca escalável de Machine Learning.
* **GraphX:** Processamento de gráficos e redes.

---

## Exemplo de Fluxo de Trabalho no Projeto

No contexto deste trabalho, o PySpark atua como o motor que lê os dados brutos e os escreve nos formatos **Delta** e **Iceberg**.

### Exemplo de código para leitura e escrita:

```python
from pyspark.sql import SparkSession

# Iniciando a sessão do Spark configurada para Delta/Iceberg
spark = SparkSession.builder \
    .appName("TrabalhoEngDados") \
    .get_factory()

# 1. Lendo uma fonte de dados (exemplo CSV)
df = spark.read.csv("dados_vendas.csv", header=True, inferSchema=True)

# 2. Transformação simples: Filtrando vendas acima de 100 reais
df_filtrado = df.filter(df["valor_total"] > 100)

# 3. Exibindo os dados processados
df_filtrado.show()

# 4. Salvando o resultado em formato Delta
df_filtrado.write.format("delta").save("/mnt/delta/vendas_processadas")
Benefícios para a Engenharia de Dados
O uso do PySpark neste projeto garante que o pipeline de dados seja:

Escalável: Pode crescer conforme o volume de dados aumenta.

Versátil: Suporta integração com diversos formatos de arquivos e bancos de dados.

Rápido: Utiliza processamento em memória para otimizar a performance.