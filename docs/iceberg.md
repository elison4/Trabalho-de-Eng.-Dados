# Apache Iceberg - Catálogo de Games e Snapshots

O **Apache Iceberg** é um formato de tabela aberto de alta performance para grandes conjuntos de dados analíticos. Diferente de formatos tradicionais, o Iceberg rastreia arquivos individuais em vez de diretórios, permitindo recursos avançados de isolamento e atomicidade.



## 1. Estrutura e Definição (DDL)
A tabela foi criada utilizando o catálogo `local` definido no Spark, garantindo que o esquema seja rigidamente seguido.

```sql
CREATE TABLE IF NOT EXISTS local.db_projeto.tabela_jogos (
    id bigint,
    nome string,
    genero string,
    ano int
) 
USING iceberg;
2. Manipulação de Dados e Consistência (DML)
O Iceberg permite operações de escrita simultâneas seguras. No projeto, validamos o fluxo completo:

Inserção: Carga inicial de títulos (FIFA, God of War, Minecraft).

Atualização: Correção do gênero do jogo 'Minecraft' para 'Construção'.

Exclusão: Remoção do registro do jogo 'FIFA 23'.

SQL
-- Exemplo de atualização de registro único
UPDATE local.db_projeto.tabela_jogos 
SET genero = 'Construção' 
WHERE id = 3;
3. Gestão de Metadados e Auditoria
O grande diferencial do Iceberg é a forma como ele gerencia o estado da tabela através de Snapshots.

Inspeção de Snapshots
Cada operação de escrita gera um novo snapshot_id. Isso permite auditoria total:

SQL
SELECT committed_at, snapshot_id, operation 
FROM local.db_projeto.tabela_jogos.snapshots;
Otimização e Limpeza (Maintenance)
Diferente do Delta, no Iceberg é comum realizarmos a manutenção de snapshots e a expiração de arquivos antigos para economizar espaço e melhorar a performance de leitura:

Python
# Exemplo de expiração de snapshots antigos via PySpark
spark.sql("CALL local.system.expire_snapshots('db_projeto.tabela_jogos')")
4. Por que usamos Iceberg neste cenário?
Schema Evolution: Se precisarmos adicionar uma coluna "Plataforma" no futuro, o Iceberg faz isso sem precisar reescrever os dados antigos.

Partition Evolution: Permite mudar a forma como os dados são particionados sem quebrar as consultas existentes.

Hidden Partitioning: O Spark/Iceberg decide automaticamente como organizar os dados para máxima performance.