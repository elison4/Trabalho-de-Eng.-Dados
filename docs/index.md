# Projeto: Arquiteturas de Dados Modernas
Este projeto explora o uso de **Delta Lake** e **Apache Iceberg** com **PySpark**.

### Cenário de Dados e Modelo ER
Utilizamos um cenário de **E-commerce**.
- **Fonte de Dados:** Arquivos brutos de vendas (JSON).
- **Modelo de Dados:**
    - **Fato_Vendas:** Contém `id_venda`, `id_produto`, `valor` e `data`.
    - **Dim_Produtos:** Contém `id_produto`, `nome` e `categoria`.