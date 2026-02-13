# AluraFood - Microserviço de Pagamentos

Este é o microserviço de pagamentos da plataforma AluraFood. Ele é responsável por gerenciar todo o fluxo de processamento de pagamentos dos pedidos realizados na plataforma.

## 🛠️ Tecnologias Utilizadas

- **Java 17**: Linguagem de programação principal.
- **Spring Boot 2.7.x**: Framework para construção do microserviço.
- **Spring Data JPA**: Para persistência de dados.
- **MySQL**: Banco de dados relacional.
- **Flyway**: Gerenciamento de migrações de banco de dados.
- **ModelMapper**: Mapeamento entre entidades e DTOs.
- **Lombok**: Redução de código boilerplate.
- **Netflix Eureka Client**: Service discovery para integração com o ecossistema de microserviços.
- **Bean Validation**: Validação de dados de entrada.

## 🚀 Como Executar

### Pré-requisitos

- Java 17 instalado.
- Maven instalado (ou use o `mvnw` incluso).
- MySQL rodando (preferencialmente na porta 3307 conforme `application.properties`).
- Eureka Server rodando na porta 8081 (opcional para execução isolada, mas recomendado).

### Passos para execução

1. Clone o repositório.
2. Certifique-se de que o MySQL está ativo e com o banco `alurafood-pagamento` criado (ou deixe o Spring JPA criar automaticamente).
3. Execute o comando Maven para rodar a aplicação:

```bash
./mvnw spring-boot:run
```

A aplicação subirá em uma porta aleatória (`server.port=0`) e se registrará no Eureka Server.

## 🔌 Endpoints da API

| Método | Endpoint | Descrição |
| :--- | :--- | :--- |
| `GET` | `/pagamentos` | Lista todos os pagamentos (paginado). |
| `GET` | `/pagamentos/{id}` | Detalha um pagamento específico. |
| `POST` | `/pagamentos` | Cria um novo pagamento. |
| `PUT` | `/pagamentos/{id}` | Atualiza os dados de um pagamento. |
| `DELETE` | `/pagamentos/{id}` | Remove um pagamento do sistema. |

### Exemplo de Payload para Criação (POST)

```json
{
  "valor": 150.50,
  "nome": "João da Silva",
  "numero": "1234567890123456",
  "expiracao": "12/28",
  "codigo": "123",
  "status": "CRIADO",
  "pedidoId": 1,
  "formaDePagamentoId": 1
}
```

## 🗄️ Estrutura do Banco de Dados

O banco de dados é gerenciado pelo Flyway. A tabela principal é `pagamentos` e contém:
- `id`: Identificador único.
- `valor`: Valor do pagamento.
- `nome`: Nome impresso no cartão.
- `numero`: Número do cartão.
- `expiracao`: Data de expiração.
- `codigo`: Código de segurança (CVV).
- `status`: Estado atual do pagamento (CRIADO, CONFIRMADO, CANCELADO).
- `pedidoId`: Referência ao pedido original.
- `formaDePagamentoId`: Referência à forma de pagamento escolhida.
