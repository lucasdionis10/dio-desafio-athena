# **Parte prática do desafio**

## **Arquitetura / Fluxo dos dados**

Repositório S3 >> Obter dados e gerar esquema com o Glue >> Realizar consultas SQL com o Athena >> Apresentar dados consultados com o QuickSight.  

****

*Se possível manter o idioma da interface em Inglês para preservar os termos técnicos.*

****

### Criando um repositório/bucket no Amazon S3

- Amazon S3 Console -> Buckets -> Create bucket -> Bucket name [nome_do_bucket] - Create bucket.
  
- Create folder (Criar uma pasta chamada ```/output``` e outra com o nome do conjunto de dados("population" no caso). Este nome irá definir o nome da tabela criada no Glue)
- Upload dos arquivos de dados localizados na pasta ```/data```

#### Criando Glue Crawler

- Amazon Glue Console -> Crawlers -> Add Crawler -> Crawler name [nome_do_crawler]
- Source type [Data Stores] -> Repeat crawls of S3 data stores [Crawl all folders] (busca em todos os arquivos do s3)
- Data store [S3] -> Include path [caminho do diretório dos dados de entrada] (selecionar a pasta, no caso "population")
- Data store [no]
- Create IAM Role (nova role, no caso chamada "population")
- Frequency [Run on demand] (periodicidade das buscas por novos dados)
- Add DB -> Database name [seu_nome_de_db] (no caso "populationdb") 
- Group behavior [Create a single schema for each S3 path] (cria esquema para todos os dados em arquivos diferentes)
- Finish
- crawler -> run crawler
- Databases -> Tables -> Visualizar dados das tabelas criadas


### Criando aplicação no Amazon Athena
**Requer setup de resultados das queries:*

Query editor -> Settings -> Manage settings -> Query result location and encryption -> Browse S3 -> selecionar o bucket criado (no caso "outpút")

*Com o setup feito, agora será possível executar as queries*

- Selecionar Database -> criar queries (exemplos na pasta ```/src```)
- Verificar queries não salvas no bucket criado no S3
- Salavar queries [nome_da_query] -> Executar novamente -> Verificar no bucket criado no S3 (serve para gerar insights a partir de resultados filtrados de queries)

#### Criando nova tabela

- Generate table DDL
- Copiar a query gerada
- Selecionar o DB e criar a nova tabela em uma nova query

### Visualizando dados no Amazon QuickSight

**Se atentar à região, selecionar a mesma localização do banco de dados para que seja integrado de forma adequada*

- Signup (caso não tenha conta) -> Escolher [Standard]
- Datasets -> Create new dataset -> Athena -> Name [NomeDoDataSet] -> Create
- Select database (conferir se a região está correta) -> select table (populationdb) ->[direct_query_data] Edit or preview -> Save & visualize
- Criar visualizações selecionando colunas, criando filtros e parâmetros e selecionando Visual types para gráficos; podendo exportar, publicar, compartilhar, entre outros recursos.

### Eliminando recursos
 - Exluir os elementos criados