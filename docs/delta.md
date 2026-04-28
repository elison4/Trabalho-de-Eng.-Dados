# Delta Lake - Gestão de Frota Automotiva

O **Delta Lake** foi utilizado para gerenciar os dados de uma frota de carros, permitindo transações seguras e o rastreamento completo de alterações através do histórico de versões.

## 1. Estrutura dos Dados (Modelo ER)
A tabela `tabela_delta_trabalho` armazena informações básicas dos veículos:
- **id**: Identificador único do veículo.
- **marca**: Fabricante do carro.
- **modelo**: Nome do modelo.
- **ano**: Ano de fabricação.

---

## 2. Operações Práticas (DML)

Abaixo, os comandos executados via PySpark para manipulação da tabela:

### Inserção Inicial
Os dados foram carregados inicialmente com modelos como Toyota Corolla, Honda Civic e Ford Focus.

```python
# Escrita inicial em formato Delta
df_carros.write.format("delta").mode("overwrite").save("../tabela_delta_trabalho")
Atualização (UPDATE)
Nesta etapa, alteramos o modelo do veículo com id = 1 para uma versão mais específica.

Python
from delta.tables import *
dt = DeltaTable.forPath(spark, "tabela_delta_trabalho")

dt.update(
    condition="id = 1", 
    set={"modelo": "'Corolla Híbrido'"}
)
Exclusão (DELETE)
Removemos o veículo da marca Ford da nossa base de dados ativa.

Python
dt.delete("id = 3")
3. Auditoria e Time Travel (Diferencial Delta)
Um dos grandes recursos utilizados foi o Time Travel, que permite visualizar estados anteriores da tabela.

Verificando o Histórico
O comando history() permite auditar quem fez o quê e quando:

Python
dt.history().select("version", "timestamp", "operation").show()
Consultando Versões Passadas
Conseguimos recuperar os dados exatamente como estavam antes das alterações de Update e Delete:

Python
# Acessando a versão 1 (Antes da limpeza dos dados)
df_passado = spark.read.format("delta") \
    .option("versionAsOf", 1) \
    .load("tabela_delta_trabalho")
Benefícios Observados
Confiabilidade: As operações de Delete e Update foram atômicas.

Auditabilidade: O histórico detalhado permite reverter erros ou conferir mudanças.

Flexibilidade: O uso do overwriteSchema permitiu evoluir a tabela quando necessário.