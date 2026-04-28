# Projeto APACHE SPARK COM DELTA LAKE E APACHE ICEBERG
 

Este repositório contém o trabalho prático de Engenharia de Dados focado na implementação e comparação de arquiteturas **Lakehouse**. O objetivo é demonstrar o uso de tabelas abertas para garantir transações ACID, evolução de esquema e viagem no tempo (Time Travel).

---

##  Tecnologias e Versões

Para que o ambiente seja reproduzido com fidelidade, foram utilizadas as seguintes ferramentas e versões:

* **Linguagem:** Python 3.10+
* **Processamento de Dados:** PySpark 3.5.0
* **Formatos de Tabela:**
    * Delta Spark 3.0.0
    * Apache Iceberg (Spark Runtime 3.5)
* **Gerenciador de Dependências:** Poetry (Garante a paridade de versões entre máquinas)

---

##  Passo a Passo para Reprodução do Ambiente

Siga rigorosamente os passos abaixo para preparar o ambiente localmente:

### 1. Pré-requisitos
Antes de começar, você deve ter instalado em sua máquina:
* **Java JDK 11 ou 17:** Essencial para a execução do motor Spark.
* **Poetry:** Caso não tenha, instale via pip: `pip install poetry`.

### 2. Clonagem e Instalação
No seu terminal (Ubuntu/WSL ou terminal do VS Code), execute:

```bash
# 1. Clone o repositório
git clone [https://github.com/elison4/Trabalho-de-Eng.-Dados.git](https://github.com/elison4/Trabalho-de-Eng.-Dados.git)

# 2. Acesse a pasta do projeto
cd Trabalho-de-Eng.-Dados

# 3. Instale as dependências exatas (o Poetry lerá o arquivo poetry.lock)
poetry install
3. Execução
Com as dependências instaladas, ative o ambiente virtual e inicie o Jupyter Notebook:

Bash
# Ativar o ambiente virtual isolado
poetry shell

# Iniciar o servidor do Jupyter
jupyter notebook
📂 Estrutura do Repositório
O projeto está organizado da seguinte forma para facilitar a navegação:

notebooks/: Pasta principal contendo os experimentos.

deltalake.ipynb: Implementação de tabelas Delta, testes de ACID e Time Travel.

iceberg.ipynb: Configuração de catálogos e manutenção de tabelas Iceberg.

pyproject.toml & poetry.lock: Arquivos de configuração que travam as versões das bibliotecas.

.gitignore: Configurado para excluir pastas pesadas (pyspark_env/) e metadados locais.

🧪 Conceitos Implementados
Transações ACID: Garantia de que as escritas nas tabelas sejam atômicas.

Time Travel: Consulta de versões históricas dos dados utilizando o log de transações.

Lakehouse Architecture: Armazenamento de dados em formato aberto (Parquet) com camada de metadados inteligente.

✒️ Autor
Elison Miller - GitHub


---

### Como finalizar no terminal:

Depois de colar e salvar o arquivo, não esqueça de avisar o GitHub:

1. `git add README.md`
2. `git commit -m "docs: adicionando instruções de reprodução do ambiente"`
3. `git push`

**Dica:** No VS Code, você pode apertar `Ctrl + Shift + V` para ver como ele ficou bonitão antes de subir! Conseguiu colar?