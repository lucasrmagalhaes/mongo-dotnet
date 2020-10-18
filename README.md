# MongoDB + .NET

### Objetivos:
1. Entender a relação frontend e backend.
2. Banco de dados.
3. MongoDB.
4. Mão na massa.

### Front vs Backend:
- Front: Web, Mobile e Service.
- API
- Back: DB, Service e File.

### API:
- Application Programming Interface

	“As APIs proporcionam a integração entre sistemas que possuem linguagem totalmente distintas de maneira ágil e segura. Em outras formas de integração de sistemas, o profissional que realiza o trabalho precisa, muitas vezes, instalar recursos compatíveis com o sistema no qual se busca efetuar a integração”

- https://vertigo.com.br/o-que-e-api-entenda-de-uma-maneira-simples/

### Bancos Relacionais:
- Microsoft SQL Server
- MySQL
- PostgreSQL
- Oracle

### Bancos não Relacionais:
- NoSQL – Not Only SQL
- Classe de banco de dados que fornecem um mecanismo para armazenamento e recuperação de dados que são modelados de formas diferentes das relações tubulares usadas nos bancos de dados relacionais.
- Tais bancos existem desde o final da década de 1960, mas não obtiveram o apelido de “NOSQL” até atingirem dua onde popularidade no início do século 21, desencadeada pelas necessidades das empresas de Web 2.0 como Facebook, Google e Amazon.com.

### Origem do termo NoSQL:
- O termo NoSQL foi usado por Carlo Strozzi em 1998 para nomear seu banco de dados relacional open source, chamado Strozzi NoSQL, que não expôs a interface padrão da linguagem de consulta estruturada (SQL), mas ainda era relacional.

### Por que usar NoSQL e não SQL:
- Performance
- Escalabilidade
- Flexibilidade
- Agilidade de desenvolvimento

### Classes NoSQL:
- Atualmente existem mais de 200 bancos NoSQL!

### Existem 4 classes de NoSQL:
- Chave/Valor (Key-Value) | redis
- Colunas (Column Family) | cassandra
- Documento (Document model) | mongoDB
- Grafos (Graph) | neo4j

### Ranking DB:
- https://www.db-engines.com/en/ranking

### Backend:
- Banco de Dados
- Integrações
- Cache
- Processamentos paralelos, em batch, etc.
- Mensageria
- Serviços, Cloud
- Regras de Negócio
- Etc...

### Mongo DB:
- Document Model / Multi-model
- Escrito em C++
- Opensource – https://github.com/mongodb/mongo
- Multi-plataforma
- Armazena dados em formato BSON
- Versões: Community e Enterprise. - https://docs.mongodb.com/manual/installation/

### MongoDB Atlas:
- https://www.mongodb.com/cloud/atlas
- Totalmente gerenciado
- Consegue colocar na mesma vpc na cloud (GCP, Azure ou AWS)
- Versão Enterprise
- Tem o mongo stitch (tipo serverless em node)
- Dá para ativar o charts: cria dashboards, paga por uso (até 1GB por mês é grátis → 500 mil views)
- Tem command line tools
- Estrutura: projeto > cluster > user > database

### Terminologia:
- Relational DB – Base de Dados, Tabela, Registro e Coluna.
- MongoDB – Base de Dados, Coleção, Documento e Atributo.

### Standalone:
- Atende aplicações que não necessitam de escalabilidade e alta disponibilidade.
- Possui apenas um mongod em execução.
- Não é indicado para produção.

### Replicaset:
- Um conjunto de mongod que armazena os mesmos dados.
- A replicação fornece redundância e aumenta a disponibilidade dos dados.
- Fornece um nível de tolerância a falhas contra a perda de um único servidor de banco de dados.
- Recomendado para a maioria dos ambientes produtivos.
- Alguns deploys podem configurados para aumentar a capacidade de leitura.

### Insert:
for (var i=0; I<=25; i++) db.contador.insert({x:i})

db.products.insert({ProdctName:”Caixa”,Price:20})

db.products.insertMany([
	{ productName: “Lapis”, stock: 10, price: 20, status: “A” },
	{ productName: “Tesoura”, prince: 5, status: “B” },
	{ productName: “Borracha”, price: 15, status: “A” }
])

### Find:
db.contador.find().pretty()
SELECT * FROM contador

db.products.find({ status:”A”})
SELECT * FROM products WHERE status = “A”

db.products.find({ status: { $in: [“A”, “B”]  } })
SELECT * FROM products WHERE status in (“A”, “B”)

### MongoDB Compass:
- https://www.mongodb.com/download-center/compass
- Para realizar querying e avaliar schemas e aggregations

### Mão na massa:
1. Acessar e se cadastrar no MongoAtlas: https://www.mongodb.com/cloud/atlas
2. Criar o projeto: mongo-api
3. Criar o Cluster – Google Cloud – São Paulo
4. dotnet --version
5. $ dotnet new api -n Api
6. $ cd Api/
7. code .
8. MongoAtlas → Database Access → Add → user: api e password: 0v0iIx1vtdZsJKPy
9. Network Access → Allow Access From Anywhere
10. Clusters – Connect – Connect with your application – C#/.NET – Versão mais recente
11. mongodb+srv://api:0v0iIx1vtdZsJKPy@cluster0.cyimu.gcp.mongodb.net/<dbname>?retryWrites=true&w=majority
12. https://github.com/mongodb/mongo-csharp-driver
13. dotnet add package MongoDB.Driver
14. https://http.cat/
15. F5 ou dotnet run
16. Como é uma aplicação Backend para testar, utilizar a ferramenta Postman.
17. POST – Body – raw - JSON
{
        "dataNascimento": "1990-03-01",
        "sexo": "M",
        "latitude": -23.5630994,
        "longitude": -46.6565712
}
18. Acessar o MongoAtlas e ir em Clusters – Collections para ver os dados adicionados.
19. Postman: GET – Body – None.
20. MongoAtlas - Gráfico: Chart - Data Sources, selecionar o Banco. Após criar um Dashboard.
