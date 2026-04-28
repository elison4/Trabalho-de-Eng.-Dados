# Apache Spark (PySpark)

O **Apache Spark** é o motor de processamento distribuído que sustenta este projeto. Através da biblioteca **PySpark**, conseguimos manipular dados em larga escala e integrá-los nativamente com os formatos **Delta Lake** e **Apache Iceberg**.

## O Papel do Spark no Projeto
Neste ecossistema, o Spark atua como a camada de computação, permitindo:
1. **Abstração de Dados:** Uso de DataFrames para manipulação de listas complexas.
2. **Execução SQL:** Interação direta com catálogos Iceberg através de comandos ANSI SQL.
3. **Multi-Formato:** Capacidade de ler e escrever em diferentes formatos de tabela no mesmo pipeline.

---

## Exemplo de Integração Multi-Formato

O código abaixo exemplifica como o PySpark foi utilizado para processar os dois cenários distintos do trabalho:

```sql
from pyspark.sql import SparkSession
```

# 1. Operação com Delta Lake (Uso de DataFrame API)
dados_carros = [(1, "Toyota", "Corolla", 2020)]
df_carros = spark.createDataFrame(dados_carros, ["id", "marca", "modelo", "ano"])

df_carros.write.format("delta").mode("overwrite").save("../tabela_delta_trabalho")

# 2. Operação com Apache Iceberg (Uso de Spark SQL)

spark.sql("""
    INSERT INTO local.db_projeto.tabela_jogos VALUES
    (1, 'FIFA 23', 'Esporte', 2023)
""")

Benefícios da Arquitetura Unificada
Ao utilizar o PySpark como motor central, garantimos:

Escalabilidade: O processamento pode ser distribuído em clusters caso o volume de carros ou jogos cresça.

Flexibilidade: O Spark permite transitar dados entre Delta e Iceberg conforme a necessidade técnica do projeto.

Performance: O uso do otimizador Catalyst do Spark garante que as operações de JOIN e FILTRO sejam executadas da forma mais rápida possível em ambos os formatos.