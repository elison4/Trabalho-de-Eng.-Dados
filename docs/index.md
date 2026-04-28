# Projeto: Arquiteturas de Dados Modernas (Delta vs Iceberg)

Este projeto apresenta a implementação prática de duas das principais tecnologias de **Table Format** do mercado, integradas com o motor de processamento **Apache Spark**.

## Objetivo
Demonstrar a capacidade de realizar operações transacionais (ACID) em ambientes de Big Data, incluindo criação, inserção, atualização e deleção de registros, além de explorar o histórico de dados (Time Travel).

---

## Cenários de Dados Implementados

Para evidenciar a versatilidade das ferramentas, o projeto foi dividido em dois domínios distintos:

### 1. Gestão de Frota Automotiva (Delta Lake)
* **Objetivo:** Controlar o inventário de veículos e rastrear mudanças de modelos.
* **Destaque Técnico:** Uso de *Time Travel* para recuperar versões anteriores da tabela.
* **Entidade:** `id`, `marca`, `modelo`, `ano`.

### 2. Catálogo de Games (Apache Iceberg)
* **Objetivo:** Gerenciar um catálogo de jogos eletrônicos e seus gêneros.
* **Destaque Técnico:** Gestão de *Snapshots* para auditoria de operações.
* **Entidade:** `id`, `nome`, `genero`, `ano`.

---

## Modelo Entidade-Relacionamento (ER)

Embora as tabelas operem em contextos diferentes, ambas seguem o modelo de **Tabela Única de Fatos (Flat Table)** para otimização de consultas analíticas:

| Domínio | Tabela | Chave Primária | Atributos Principais |
| :--- | :--- | :--- | :--- |
| **Carros** | `tabela_delta_trabalho` | `id` | marca, modelo, ano |
| **Jogos** | `tabela_jogos` | `id` | nome, genero, ano |

---

## Tecnologias Utilizadas
* **Linguagem:** Python (PySpark)
* **Processamento:** Apache Spark 3.x
* **Armazenamento:** Delta Lake & Apache Iceberg
* **Documentação:** MkDocs Material