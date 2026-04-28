# Projeto: Apache Spark com Delta Lake e Apache Iceberg 🚀

Este repositório contém o trabalho prático para a disciplina de Engenharia de Dados. O objetivo é a criação de um ambiente unificado utilizando **PySpark** e **Jupyter** para a implementação e manipulação de dados nos formatos **Delta Lake** e **Apache Iceberg**.

---

## 👥 Integrantes do Grupo
* **Elison Miller** -(https://github.com/elison4)
* **Guilherme Cesarino** 


---

## 🛠️ Especificações do Ambiente

Para garantir a reprodutibilidade (conforme solicitado), o projeto utiliza o **Poetry** para travar as versões das bibliotecas:

* **Processamento:** PySpark 3.5.0
* **Delta Lake:** Delta Spark 3.0.0
* **Apache Iceberg:** Spark Runtime 3.5
* **IDE/Interface:** Jupyter Lab / VS Code Jupyter Extension
* **Python:** 3.12.3

---

## 🚀 Passo a Passo para Reprodução

### 1. Pré-requisitos
* **Java JDK 11 ou 17** (Necessário para o motor do Spark).
* **Poetry** instalado (`pip install poetry`).

### 2. Instalação
No terminal, dentro da pasta do projeto:
```bash
# Instala as dependências exatas do arquivo poetry.lock
poetry install
3. Execução
Bash
# Ativa o ambiente virtual
poetry shell

# Inicia o Jupyter Lab ou Notebook
jupyter notebook
📂 Estrutura do Projeto
Conforme solicitado, o projeto está dividido em:

notebooks/deltalake.ipynb: Implementação das funcionalidades do Delta Lake.

notebooks/iceberg.ipynb: Implementação das funcionalidades do Apache Iceberg.

pyproject.toml: Lista detalhada de todas as bibliotecas e dependências.