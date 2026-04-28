# Apache Iceberg

O **Apache Iceberg** é um formato de tabela aberto de alto desempenho para enormes tabelas analíticas. Ele permite que o SQL trabalhe com grandes volumes de dados de forma eficiente, oferecendo funcionalidades que antes só existiam em bases de dados tradicionais.

## O que é o Apache Iceberg?
Diferente dos formatos comuns, o Iceberg foca-se na gestão de ficheiros de metadados, o que permite:
- **Time Travel:** Consultar versões anteriores dos dados.
- **Schema Evolution:** Alterar colunas sem reescrever toda a tabela.
- **Partition Evolution:** Mudar a forma como os dados são organizados sem quebrar as consultas.

---

## Demonstração Prática (Cenário de Vendas)

Abaixo, apresentamos os comandos necessários para gerir uma tabela de produtos utilizando o motor do Spark.

### 1. Criação da Tabela (DDL)
Aqui definimos a estrutura da nossa tabela dentro do catálogo Iceberg.

```sql
CREATE TABLE local.db.produtos_iceberg (
    id_produto INT,
    nome_produto STRING,
    categoria STRING,
    preco_unitario DOUBLE
) 
USING iceberg;

2. Inserção de Dados (INSERT)
Adicionando novos itens ao nosso catálogo de produtos.

SQL
INSERT INTO local.db.produtos_iceberg VALUES 
(101, 'Teclado Mecânico', 'Periféricos', 250.00),
(102, 'Monitor 4K', 'Hardware', 1800.00),
(103, 'Mouse Gamer', 'Periféricos', 150.00);
3. Atualização de Dados (UPDATE)
Corrigindo o preço de um produto específico.

SQL
UPDATE local.db.produtos_iceberg 
SET preco_unitario = 230.00 
WHERE id_produto = 101;
4. Exclusão de Dados (DELETE)
Removendo um produto que saiu de linha.

SQL
DELETE FROM local.db.produtos_iceberg 
WHERE id_produto = 103;
Porquê usar Iceberg com Spark?
A integração do PySpark com Iceberg garante que as operações acima sejam atómicas. Isso significa que, se uma atualização falhar a meio, a tabela não fica corrompida; ela volta ao estado anterior (Transações ACID).