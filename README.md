# Projeto: Implementação de Lakehouse com Apache Spark 🚀
### Tecnologias: Delta Lake & Apache Iceberg

Este repositório contém o trabalho prático da disciplina de Engenharia de Dados. O objetivo é configurar um ambiente unificado de Big Data para manipular tabelas nos formatos **Delta Lake** e **Apache Iceberg**, garantindo a integridade dos dados e funcionalidades avançadas de armazenamento.

---

## 👥 Integrantes do Grupo
* **Elison Miller** - [GitHub](https://github.com/elison4)
* **Guilherme Cesarino**

---

##  Especificações Detalhadas do Ambiente

Para atender aos requisitos de reprodutibilidade, o ambiente foi isolado utilizando **Poetry**. Abaixo, detalhamos as versões exatas de cada componente do ecossistema:

### 1. Linguagem e Runtime
* **Python:** `3.12.3` (Gerenciado via ambiente virtual `.venv`)
* **Java (JDK):** `11` ou `17` (Requisito obrigatório para execução do binário do Spark)

### 2. Core do Spark & Bibliotecas de Dados
* **PySpark:** `3.5.0`
* **Delta Spark:** `3.0.0`
* **Apache Iceberg:** `spark-runtime 3.5`

---

## 🚀 Passo a Passo para Reprodução (Deployment)

### Passo 1: Clonar e Preparar o Repositório
```bash
git clone [https://github.com/elison4/Trabalho-de-Eng.-Dados.git](https://github.com/elison4/Trabalho-de-Eng.-Dados.git)
cd Trabalho-de-Eng.-Dados
```
Passo 2: Instalação via Poetry

```Bash
# Sincroniza as dependências e instala as bibliotecas
poetry lock
poetry install
Passo 3: Ativação e Execução
Bash
# Ativa o ambiente
poetry shell
```
# Inicia o servidor dos Notebooks
```bash
poetry run jupyter lab
```
⚠️ Resolução de Problemas (Troubleshooting)
Caso encontre erros de ambiente (comuns em distribuições Linux com Python 3.12+), utilize os comandos abaixo:

## 1. Erro de Ambiente Gerenciado (PEP 668)
Se o Linux impedir a instalação de pacotes globais, instale o Poetry via instalador oficial:

```Bash
curl -sSL [https://install.python-poetry.org](https://install.python-poetry.org) | python3 -
export PATH="$HOME/.local/bin:$PATH"
```
## 2. Conflito de Versão no Poetry (posixpath)
Se o comando poetry install falhar, limpe o cache e force a versão do Python 3.12:

```Bash
rm -rf .venv poetry.lock
poetry env use python3.12
poetry lock
poetry install
```

## 📂 Estrutura do Projeto
deltalake.ipynb: Operações de escrita/leitura, manutenção (Vacuum/Optimize) e Time Travel.

iceberg.ipynb: Configuração de catálogos locais, evolução de esquema e gestão de snapshots.

⚙️ Configuração Técnica
As configurações de spark.jars.packages necessárias para o funcionamento foram incluídas diretamente nos notebooks, apontando para os repositórios Maven oficiais.