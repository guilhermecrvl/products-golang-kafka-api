# Go Kafka Product Service

Este é um aplicativo Go simples que demonstra o uso do Kafka para comunicação assíncrona entre microsserviços. O aplicativo permite criar e listar produtos usando pontos de extremidade HTTP e consome mensagens de um tópico Kafka para criar produtos de forma assíncrona.

## Recursos

- **Servidor HTTP**: Manipula solicitações HTTP para criar e listar produtos.
- **Banco de Dados MySQL**: Armazena dados de produtos de forma persistente.
- **Integração com Kafka**: Consome mensagens de um tópico Kafka para criar produtos de forma assíncrona.

## Pré-requisitos

- Go instalado em sua máquina ([instruções de instalação](https://golang.org/doc/install))
- Docker instalado em sua máquina ([instruções de instalação](https://docs.docker.com/get-docker/))
- Servidor MySQL em execução com o banco de dados `products` disponível em `host.docker.internal:3306`.
- Broker Kafka em execução em `host.docker.internal:9094`.
- `librdkafka-dev` instalado no contêiner Docker.

## Instalação

1. Clone o repositório:

   ```bash
   gh repo clone guilhermecrvl/products-golang-kafka-api
   ```

gh repo clone guilhermecrvl/products-golang-kafka-api

2. Compile a imagem Docker:

   ```bash
   docker build -t go-kafka-product-service .
   ```

3. Execute o contêiner Docker:

   ```bash
   docker run -d --name go-kafka-product-service go-kafka-product-service
   ```

## Uso

O aplicativo expõe os seguintes pontos de extremidade HTTP:

- `POST /products`: Cria um novo produto. Envie um payload JSON com o nome e o preço do produto.
- `GET /products`: Recupera uma lista de todos os produtos.

## Configuração

Certifique-se de que as seguintes variáveis de ambiente estejam definidas:

- `MYSQL_DSN`: Nome da fonte de dados do MySQL (`root:root@tcp(host.docker.internal:3306/products)`).
- `KAFKA_BROKERS`: Lista de brokers Kafka separados por vírgula (`host.docker.internal:9094`).
- `KAFKA_TOPICS`: Lista de tópicos Kafka para consumir, separados por vírgula (`products`).

## Licença

Este projeto é licenciado sob a Licença MIT - consulte o arquivo [LICENSE](LICENSE) para obter detalhes.
