# Eureka Server - Alurafood

Este é o servidor de Service Discovery (Eureka Server) para o ecossistema de microserviços do Alurafood. Ele permite que os microserviços se registrem e descubram uns aos outros dinamicamente.

## 🛠️ Tecnologias
- **Java 17**
- **Spring Boot 2.7.18**
- **Spring Cloud 2021.0.8** (Netflix Eureka Server)
- **Maven**

## ⚙️ Configurações
O servidor está configurado no arquivo [application.properties]com as seguintes definições principais:

- **Porta:** 8081
- **Auto-preservação:** Desativada (`eureka.server.enableSelfPreservation=false`)
- **Registro Próprio:** Desativado (como é o servidor central, ele não se registra em si mesmo)

## 🚀 Como executar

### Pré-requisitos
- JDK 17 instalado
- Maven (opcional, pois o projeto inclui o Maven Wrapper)

### Comandos
Para rodar a aplicação, navegue até a pasta `server` e utilize:

**Windows (PowerShell):**
```powershell
.\mvnw.cmd spring-boot:run
```

**Linux/Mac:**
```bash
./mvnw spring-boot:run
```

## 📊 Acesso ao Painel
Após a inicialização, você pode acessar o dashboard do Eureka para visualizar os serviços registrados em:
👉 [http://localhost:8081](http://localhost:8081)

---
*Projeto desenvolvido para fins de estudo sobre arquitetura de microserviços.*
