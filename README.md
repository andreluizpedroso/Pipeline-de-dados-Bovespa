# 🚀 Tech Challenge - Pipeline de Dados para Bovespa

## 📌 Visão Geral
Este projeto consiste na construção de um **pipeline de dados completo** para extrair, processar e analisar os dados do pregão da B3 (**Bovespa**). A solução será implementada tanto na **AWS** quanto no **Google Cloud**, permitindo comparação entre as duas arquiteturas.

## 🎯 Objetivos
- 🕵️‍♂️ Extrair dados do pregão da B3 via **scraping**.
- 💾 Armazenar os dados brutos em um **data lake**.
- ⚙️ Processar e transformar os dados utilizando ferramentas de **ETL**.
- 📊 Disponibilizar os dados refinados para consulta em **SQL**.
- 📈 Criar visualizações a partir dos dados processados.

## 🛠️ Tecnologias Utilizadas
### ☁️ AWS Stack
- **Amazon S3**: Armazenamento de dados brutos e refinados.
- **AWS Lambda**: Trigger para iniciar o processamento dos dados.
- **AWS Glue**: ETL para transformação dos dados.
- **AWS Glue Catalog**: Catálogo dos metadados.
- **Amazon Athena**: Consulta SQL sobre os dados processados.
- **Amazon QuickSight** (opcional): Visualização de dados.

### ☁️ Google Cloud Stack
- **Google Cloud Storage (GCS)**: Armazenamento de dados brutos e refinados.
- **Google Cloud Functions**: Trigger para iniciar o processamento dos dados.
- **Google Cloud Dataflow / Dataprep**: ETL para transformação dos dados.
- **Google Cloud Data Catalog**: Catálogo dos metadados.
- **Google BigQuery**: Consulta SQL sobre os dados processados.
- **Looker / Google Data Studio** (opcional): Visualização de dados.

## 🔄 Estrutura do Pipeline
1. **📥 Coleta de Dados**: Web scraping dos dados da B3.
2. **💾 Armazenamento**: Salvamento dos dados brutos no formato **Parquet** com partição diária.
3. **⚡ Trigger do Processamento**: Upload dos dados dispara uma **função serverless** (AWS Lambda / Google Cloud Function).
4. **🛠️ ETL**: 
   - 🔢 Agrupamento numérico e sumarização.
   - ✏️ Renomeação de colunas.
   - 📅 Cálculo com campos de data.
5. **💾 Armazenamento dos Dados Processados**: Os dados refinados são armazenados no data lake.
6. **📂 Catalogação**: Os dados são catalogados automaticamente.
7. **🔍 Consulta SQL**: Os dados ficam disponíveis para análise no Athena ou BigQuery.
8. **📊 Visualização** (opcional): Construção de dashboards interativos.

## 🚀 Como Implementar

### 1️⃣ Implementação na AWS
#### ☁️ Configurar o Armazenamento
1. Criar um **bucket S3** para armazenar os dados.
2. Configurar permissões adequadas no bucket.

#### ⚡ Criar a Função Lambda
3. Criar uma **AWS Lambda** que dispara o job no Glue.
4. Configurar o trigger para ser ativado ao upload de arquivos no S3.

#### 🛠️ Configurar o Glue
5. Criar um **Job AWS Glue** no modo visual com as transformações necessárias.
6. Configurar a saída dos dados no bucket **refined**.
7. Criar o **Glue Catalog** para catalogar os dados automaticamente.

#### 🔍 Consulta e Visualização
8. Configurar o **Athena** para consultas SQL.
9. (Opcional) Criar dashboards no **QuickSight**.

### 2️⃣ Implementação no Google Cloud
#### ☁️ Configurar o Armazenamento
1. Criar um **bucket no Google Cloud Storage (GCS)** para armazenar os dados.
2. Configurar permissões adequadas no bucket.

#### ⚡ Criar a Função Cloud Function
3. Criar uma **Google Cloud Function** para disparar o job no Dataflow.
4. Configurar o trigger para ser ativado ao upload de arquivos no GCS.

#### 🛠️ Configurar o Dataflow
5. Criar um **pipeline Dataflow (Apache Beam)** com as transformações necessárias.
6. Configurar a saída dos dados no bucket **refined**.
7. Criar o **Data Catalog** para catalogar os dados automaticamente.

#### 🔍 Consulta e Visualização
8. Configurar o **BigQuery** para consultas SQL.
9. (Opcional) Criar dashboards no **Looker / Data Studio**.

## 📁 Estrutura do Repositório
```
/
|-- aws/                   # Implementação AWS
|   |-- lambda/            # Código da AWS Lambda
|   |-- glue/              # Configuração do Glue Job
|   |-- athena/            # Scripts SQL para consultas
|   |-- quicksight/        # Dashboards (se aplicável)
|
|-- gcp/                   # Implementação Google Cloud
|   |-- cloud_function/    # Código da Cloud Function
|   |-- dataflow/          # Pipeline Dataflow
|   |-- bigquery/          # Scripts SQL para consultas
|   |-- looker/            # Dashboards (se aplicável)
|
|-- data/                  # Exemplo de datasets
|-- notebooks/             # Jupyter Notebooks para análise
|-- README.md              # Documentação do projeto
```

## 🤝 Como Contribuir
1. Faça um **fork** do repositório.
2. Crie uma **branch** para sua feature (`git checkout -b minha-feature`).
3. Faça **commit** das suas alterações (`git commit -m 'Adiciona nova feature'`).
4. Faça um **push** para a branch (`git push origin minha-feature`).
5. Abra um **Pull Request**.

## 📩 Contato
Caso tenha dúvidas ou sugestões, entre em contato via [GitHub Issues](https://github.com/andreluizpedroso/Pipeline-de-dados-Bovespa).

---

Este projeto faz parte do **Tech Challenge - Fase 2 - Machine Learning Avançado**.

