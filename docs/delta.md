# Delta Lake
O Delta oferece transações ACID. Aqui estão os comandos obrigatórios:

**Criação da Tabela (DDL):**
```sql
CREATE TABLE vendas_delta (id INT, valor DOUBLE) USING DELTA;

Manipulação de Dados (INSERT, UPDATE, DELETE):

SQL
INSERT INTO vendas_delta VALUES (1, 150.0);
UPDATE vendas_delta SET valor = 200.0 WHERE id = 1;
DELETE FROM vendas_delta WHERE id = 1;