Este projeto demonstra a configuração completa de um ambiente de desenvolvimento local para trabalhar com **Delta Lake** e **PySpark**, utilizando o **Windows Subsystem for Linux (WSL)**.

---

## 🛠️ 1. Tecnologias e Versões Utilizadas

A tabela abaixo detalha as principais ferramentas e versões utilizadas para garantir a compatibilidade e a execução bem-sucedida do projeto.

| Ferramenta | Versão Utilizada | Finalidade |
| :--- | :--- | :--- |
| **Sistema Operacional** | WSL/Ubuntu | Ambiente Linux para execução do Python e Spark. |
| **Python** | 3.12 (Versão do `venv`) | Linguagem de programação para o projeto. |
| **PySpark** | **3.4.2** | API Python para interagir com o Apache Spark. |
| **Delta-Spark** | **2.4.0** | Conector Python para a biblioteca Delta Lake. |
| **Jupyter Lab** | Última Estável | Ambiente interativo para desenvolvimento. |
| **Delta Core JAR** | **2.4.0** | Biblioteca Scala/Java do Delta Lake (baixa via `spark.jars.packages`). |

---

## 💻 2. Setup do Ambiente e Instalação (WSL/Linux)

Todos os comandos foram executados dentro do terminal WSL/Ubuntu. O ambiente virtual (`venv`) foi criado para isolar as dependências e evitar o erro `externally-managed-environment`.

### A. Setup do ambiente virtual

#### 1. Cria o ambiente virtual
```bash
python3 -m venv delta_env
```

#### 2. Ativa o ambiente virtual
```bash
source delta_env/bin/activate
# O terminal deve mostrar: (delta_env) como prefixo
```

#### 3. Instalação das versões específicas do PySpark e Delta Lake
```bash
pip install pyspark==3.4.2 delta-spark==2.4.0 jupyterlab
```

#### 4. Configuração do Kernel para o Jupyter
Este passo é fundamental para que o Jupyter Lab reconheça o ambiente delta_env e pare de dar o erro ModuleNotFoundError: No module named 'pyspark'.
```bash
pip install ipykernel
python -m ipykernel install --user --name=delta_lake_kernel --display-name "Python (Delta Lake - delta_env)"
```

#### 5. Iniciar o Jupyter Lab
```bash
jupyter-lab
```

Após iniciar o **Jupyter Lab** (jupyter-lab), o **Kernel Python** (Delta Lake - delta_env) deve ser selecionado no *notebook*.

Ir até a página do jupyter-lab que foi inicializada no localhost e seguir os passos abaixo:
- Kernel > Change Kernel > Selecionar o Kernel `Delta Lake - delta_env` > Select.

<img width="498" height="255" alt="image" src="https://github.com/user-attachments/assets/69315e7b-c606-4bd8-847d-24d67846cf40" />

Os códigos utilizados para instanciar o Spark, criar uma tabela Delta Lake e realizar a inserção e manipulação dos dados estão no arquivo `delta.ipynb`

**Links e referências sobre a compatibilidade das versões do Apache Spark (pyspark) e Delta Lake:**
https://docs.delta.io/latest/releases.html
https://mvnrepository.com/artifact/io.delta/delta-spark
https://github.com/delta-io/delta/releases/
