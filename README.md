# 📧 Email Microservice (Java & Spring Boot)

> Microsserviço de mensageria responsável pelo disparo de notificações e e-mails de confirmação, desenvolvido em Java utilizando o ecossistema Spring.

---

## Sobre o Projeto

Microsserviço de suporte focado na comunicação assíncrona/externa da arquitetura, responsável por receber requisições com os dados de disparo de e-mails (`payload`) e processar o envio das notificações para os participantes dos eventos.

---

## Tecnologias Utilizadas

* **Java** (Versão recente recomendada)
* **Spring Boot**
* **Spring Web** (@RestController, DTOs e Mapeamento de Rotas)
* **Lombok** (Biblioteca de anotações para reduzir a escrita de códigos repetitivos)
* **Maven** (Gerenciamento de dependências)

---

## Papel na Arquitetura de Microsserviços

Este serviço atua de forma isolada e desacoplada, recebendo chamadas HTTP vindas do **Events Microservice** via **Spring Cloud OpenFeign**. 

O fluxo de operação ocorre da seguinte forma:
1. O serviço de eventos processa a inscrição de um participante e aciona seu cliente HTTP.
2. O **Email Service** recebe a requisição na porta configurada (`8090`), contendo o *payload* do e-mail com remetente, assunto e corpo da mensagem.
3. A aplicação processa a solicitação de envio da notificação correspondente.

--- 

## Endpoints da API

A aplicação disponibiliza a rota principal para recepção e disparo de e-mails:

### 1. Enviar E-mail de Notificação
* **POST** `/api/email/send`
* **Exemplo de Body (JSON):**
  ```json
  {
    "to": "usuario@email.com",
    "subject": "Confirmação de Inscrição no Evento",
    "body": "Olá! Sua inscrição foi realizada com sucesso."
  }


## Como Executar O Projeto

1. Clone este repositório:
git clone [https://github.com/larissamonsalve/email-microservice.git](https://github.com/larissamonsalve/email-microservice.git)
2. Configure a porta de execução no arquivo application.properties para rodar na porta 8090 (evitando conflito com o serviço de eventos):
  ```bash
  Properties
  server.port=8090

3. Execute a aplicação através da sua IDE (IntelliJ, Eclipse, VS Code) ou via terminal com Maven/Gradle:
    ```bash
    ./mvnw spring-boot:run
    
## Agradecimentos e Créditos

Este projeto foi desenvolvido como parte dos estudos práticos acompanhando o conteúdo e a live de microsserviços com Java ministrada pela **Fernanda Kipper** ([Fernanda-Kipper](https://github.com/Fernanda-Kipper)). Todo o passo a passo da arquitetura e lógica inicial foi baseado nos ensinamentos compartilhados por ela.