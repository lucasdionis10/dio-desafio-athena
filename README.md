# **Desafio de Projeto Athena**

### Repositório para Desafio da DIO
Aluno: Lucas Dionísio

*****

## Amazon Athena
*É um serviço serverless (o admin não precisa alocar nem dimensionar previamente nenhuma especificação técnica para seu funcionamento, a AWS se encarrega de provisionar de forma dinâmica) de consultas interativas usando SQL padrão, voltado para análise de dados do  Amazon S3.*

### **Características**
- Integrado com o Glue Data Catalog, unificando o repositório de metadados em vários serviços.
  
- Realiza o crawling (busca intensa) de fontes de dados para descobrir esquemas e preencher o Catalog com definições novas e modificadas de tabelas e partições.
  
- Mantém o versionamento do esquema.
  
- Pay as you go (pague por consulta).
  
- Amigável: SQL padrão para consultas
  
- Performance: otimizado para oferecer alta performance com o S3.
  
- Segurança: Políticas de acesso através do IAM e ACLs.
  
- Disponibilidade: recursos roteados entre diversas localizações.
  
- Consultas: em diversas fontes relacionais, estruturadas ou não.

- Integração: pode trabalhar em conjunto com diversos serviços AWS.

- Usa o Presto com suporte a SQL padrão, compatível com diversos formatos de dados (CSV, JSON, ORC, Avro e Parquet).

- Consegue lidar com análises complecas, grandes associações, funções de janelas e matrizes.

- Suporta vários tipos de dados, como BOOLEAN, TINYINT, SMALLINT, INT, INTEGER, BIGINT, DOUBLE, FLOAT, CHAR, VARCHAR, STRING, TIMESTAMP, DATE, BINARY, ARRAY, MAP, STRUCT.

- As consultas são realizadas no formato DML (Data Manipulation Language), já bem conhecida e comumente utilizada em bancos de dados.

### **Boas práticas**
- Evite arquivos grandes únicos (divida os dados em arquivos menores se puder).
- Evite muitos arquivos pequenos. 
- Leia a quantidade mínima possível a cada vez.
- Evite grandes números de colunas.
- Priorize arquivos em formatos mais eficientes, como Parquet ou ORC.

