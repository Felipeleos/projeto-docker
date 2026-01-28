🐳 Microsserviços com Spring Boot + Docker










Projeto prático demonstrando a utilização do Docker no cenário de microsserviços, simulando uma arquitetura real com serviços independentes, comunicação entre containers e banco de dados isolado.

📚 Baseado nos estudos de Docker e Microsserviços na DIO.

🧱 Arquitetura do Sistema
            ┌──────────────────────┐
            │   Order Service      │
            │      (8082)          │
            └─────────┬────────────┘
                      │ REST Call
                      ▼
            ┌──────────────────────┐
            │  Product Service     │
            │       (8081)         │
            └─────────┬────────────┘
                      │ JPA
                      ▼
            ┌──────────────────────┐
            │      MySQL DB        │
            │      (3306)          │
            └──────────────────────┘

        Todos conectados pela rede interna Docker

📦 Microsserviços
Serviço	Função
🟢 product-service	Cadastro e consulta de produtos
🔵 order-service	Serviço de pedidos que consome o product-service
🗄 MySQL	Banco de dados rodando em container
📁 Estrutura do Projeto
dio-docker-microsservices/
│
├── docker-compose.yml
│
├── product-service/
│   ├── Dockerfile
│   ├── pom.xml
│   └── src/
│
└── order-service/
    ├── Dockerfile
    ├── pom.xml
    └── src/

⚙️ Tecnologias Utilizadas

Java 17

Spring Boot

Spring Data JPA

MySQL

Docker

Docker Compose

Maven

🐳 Conceitos de Docker Aplicados

✔ Containers independentes
✔ Comunicação entre microsserviços via rede Docker
✔ Banco de dados isolado
✔ Build automatizado com Dockerfile
✔ Orquestração com Docker Compose

▶️ Como Executar o Projeto
1️⃣ Gerar os JARs

Dentro de cada serviço:

mvn clean package -DskipTests

2️⃣ Subir a aplicação completa

Na raiz do projeto:

docker compose up --build

🌐 Endpoints
Serviço	URL
Product Service	http://localhost:8081

Order Service	http://localhost:8082
🧪 Testes da API
➕ Criar Produto

POST
http://localhost:8081/products

{
  "name": "Notebook",
  "price": 3500
}

📋 Listar Produtos

GET
http://localhost:8081/products

🔄 Comunicação entre Microsserviços

GET
http://localhost:8082/orders/product/1

O order-service consulta o product-service internamente via rede Docker.

🎯 Objetivo do Projeto

Demonstrar na prática:

Arquitetura de microsserviços

Uso de Docker em ambientes distribuídos

Comunicação entre containers

Orquestração de múltiplos serviços

Cenário real usado em sistemas modernos

👨‍💻 Autor

Felipe Oliveira
🎓 Estudante de Engenharia de Software
💻 Desenvolvedor em formação focado em Backend, Cloud e Microsserviços
