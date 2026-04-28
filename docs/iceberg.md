# Apache Iceberg - Catálogo de Jogos

O **Apache Iceberg** foi implementado para gerenciar um catálogo de jogos eletrônicos. Este formato de tabela aberto foi escolhido por sua eficiência em lidar com grandes volumes de metadados e por oferecer recursos avançados de auditoria.

## 1. Estrutura da Tabela (DDL)
A tabela `tabela_jogos` foi criada no catálogo local com a seguinte estrutura:
- **id**: Identificador único do jogo.
- **nome**: Título do jogo.
- **genero**: Categoria/Gênero (Ex: Ação, Esporte).
- **ano**: Ano de lançamento.

```sql
CREATE TABLE IF NOT EXISTS local.db_projeto.tabela_jogos (
    id bigint,
    nome string,
    genero string,
    ano int
) 
USING iceberg;
2. Manipulação de Dados (DML)
Utilizamos comandos SQL padrão para gerenciar o ciclo de vida dos dados:

Inserção de Dados
Populamos a tabela com títulos populares para validar a persistência.

SQL
INSERT INTO local.db_projeto.tabela_jogos VALUES
(1, 'FIFA 23', 'Esporte', 2023),
(2, 'God of War', 'Ação', 2022),
(3, 'Minecraft', 'Sandbox', 2011);
Atualização (UPDATE)
Realizamos a correção do gênero do jogo 'Minecraft' de 'Sandbox' para 'Construção'.

SQL
UPDATE local.db_projeto.tabela_jogos 
SET genero = 'Construção' 
WHERE id = 3;
Exclusão (DELETE)
Removemos o registro do jogo 'FIFA 23' (ID 1) da tabela ativa.

SQL
DELETE FROM local.db_projeto.tabela_jogos WHERE id = 1;
3. Gestão de Snapshots e Histórico
Uma das principais vantagens do Iceberg é a capacidade de consultar os Snapshots, que registram cada alteração feita na tabela.

Verificando Snapshots
Através da tabela técnica de snapshots, conseguimos identificar o momento exato de cada operação (append, delete, overwrite):

SQL
SELECT committed_at, snapshot_id, operation 
FROM local.db_projeto.tabela_jogos.snapshots 
ORDER BY committed_at ASC;
Histórico de Versões
O Iceberg mantém um histórico que permite rastrear a linhagem dos dados ao longo do tempo:

SQL
SELECT * FROM local.db_projeto.tabela_jogos.history;
Conclusão Técnica
A implementação com Iceberg demonstrou ser extremamente eficiente para operações de linha (Update/Delete) em tabelas analíticas, garantindo a integridade dos dados e permitindo uma rastreabilidade completa via Snapshots, essencial para ambientes de produção.