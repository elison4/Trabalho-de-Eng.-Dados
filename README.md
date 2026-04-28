Markdown
# Projeto: Implementação de Lakehouse com Apache Spark 🚀
### Tecnologias: Delta Lake & Apache Iceberg

Este repositório contém o trabalho prático da disciplina de Engenharia de Dados. O objetivo é configurar um ambiente unificado de Big Data para manipular tabelas nos formatos **Delta Lake** e **Apache Iceberg**, garantindo a integridade dos dados e funcionalidades avançadas de armazenamento.

---

## 👥 Integrantes do Grupo
* **Elison Miller** - [GitHub](https://github.com/elison4)
* **Guilherme Cesarino**


---

## 🛠️ Especificações Detalhadas do Ambiente

Para atender aos requisitos de reprodutibilidade, o ambiente foi isolado utilizando **Poetry**. Abaixo, detalhamos as versões exatas de cada componente do ecossistema:

### 1. Linguagem e Runtime
* **Python:** `3.12.3` (Gerenciado via ambiente virtual `.venv`)
* **Java (JDK):** `11` ou `17` (Requisito obrigatório para execução do binário do Spark)

### 2. Core do Spark & Bibliotecas de Dados
* **PySpark:** `3.5.0`
* **Delta Spark:** `3.0.0` (Implementação oficial do protocolo Delta Lake)
* **Apache Iceberg:** `spark-runtime 3.5` (Conector para integração com o catálogo do Spark)

### 3. Gerenciamento e Interface
* **Gerenciador de Dependências:** Poetry (Arquivos `pyproject.toml` e `poetry.lock`)
* **Notebook Server:** Jupyter Notebook / Jupyter Lab

---

## 🚀 Passo a Passo para Reprodução (Deployment)

Siga rigorosamente as instruções abaixo para espelhar o ambiente de desenvolvimento:

### Passo 1: Clonar e Preparar o Repositório
Abra o terminal e execute os comandos para baixar o código e entrar na pasta raiz:
```bash
git clone [https://github.com/elison4/Trabalho-de-Eng.-Dados.git](https://github.com/elison4/Trabalho-de-Eng.-Dados.git)
cd Trabalho-de-Eng.-Dados
### Passo 2: Instalação Automática via Poetry
O Poetry irá ler o arquivo poetry.lock para instalar as bibliotecas exatamente como foram usadas no desenvolvimento, evitando conflitos de versão.

Bash
# Instala o ambiente virtual e todas as libs (PySpark, Delta, Iceberg)
poetry install
### Passo 3: Ativação do Ambiente Virtual
Para garantir que o terminal use o Python do projeto e não o do sistema:

Bash
# Entra no shell do ambiente virtual
poetry shell
Dica: Você verá o nome do ambiente (ex: .venv) aparecer no início da linha do terminal.

### Passo 4: Inicialização do Jupyter
Com o ambiente ativo, execute o comando abaixo para abrir os notebooks:

Bash
jupyter notebook
📂 Estrutura e Implementação dos Notebooks
O projeto está organizado na pasta notebooks/, contendo dois arquivos principais:

deltalake.ipynb:

Configuração do SparkSession com extensões Delta.

Operações de escrita e leitura em formato .delta.

Demonstração de comandos de manutenção (Vacuum, Optimize) e Time Travel.

iceberg.ipynb:

Configuração de catálogos (spark.sql.catalog.local).

Implementação de tabelas Apache Iceberg.

Testes de evolução de esquema e snapshots.

### ⚙️ Configuração Técnica (Interna)
As configurações de spark.jars.packages necessárias para o funcionamento foram incluídas diretamente nos notebooks para facilitar a execução, apontando para os repositórios Maven oficiais do Delta e Iceberg.