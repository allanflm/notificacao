# 📬 Microsserviço de Notificação - Spring Boot

Este projeto é um microsserviço desenvolvido para processar e enviar notificações de tarefas por e-mail. Ele utiliza o ecossistema Spring Boot para integrar o envio de e-mails com templates dinâmicos.

## 🚀 Tecnologias e Ferramentas

* **Java 17**
* **Spring Boot 3.x**
* **Spring Mail** (Jakarta Mail)
* **Thymeleaf** (Templates HTML para e-mail)
* **Lombok** (Redução de código boilerplate)
---
## ⚙️ Configuração de Segurança (Importante)

O arquivo `application.yml` contém credenciais sensíveis e está ignorado no `.gitignore`. Para rodar o projeto, crie o arquivo em `src/main/resources/application.yml` seguindo este modelo:

```yaml
spring:
  mail:
    host: smtp.gmail.com
    port: 587
    username: 'seu-email@gmail.com'
    password: 'sua-senha-de-app-16-digitos' # Não é a senha comum do Gmail!
    properties:
      mail:
        smtp:
          auth: true
          starttls:
            enable: true

envio:
  email:
    remetente: 'seu-email@gmail.com'
    nome: 'Allan Felipe'

server:
  port: 8082
```
##  🛠️ Utilização (API)
O serviço expõe um endpoint para receber os dados da tarefa e disparar o e-mail.

POST /email

Exemplo de Payload (JSON)
No Postman, envie o objeto abaixo (certifique-se de não usar colchetes [] se estiver enviando apenas um objeto):

```
JSON
{
  "id": "66b13b597760d30f094b37df",
  "nomeTarefa": "Obter Certificado Curso ...",
  "descricao": "Estudar todos os módulos do curso pra pegar o certificado",
  "dataCriacao": "05-08-2024 17:51:37",
  "dataEvento": "05-04-2024 15:00:00",
  "emailUsuario": "contato@exemplo.com",
  "statusNotificacaoEnum": "PENDENTE"
}
```

Detalhes de Implementação:
* Mapeamento: Utilizamos `@JsonProperty("nomeTarefa")` no DTO para garantir a compatibilidade entre o JSON e o código Java.
* Datas: O formato de data aceito é `dd-MM-yyyy HH:mm:ss`.

## 📁 Estrutura do Projeto
- `business`: Contém o EmailService com a lógica de envio.
- `controller`: Contém o EmailController para receber as requisições.
- `dto`: Objetos de transferência (TarefasDTO) configurados com Jackson.

resources/templates: Templates HTML processados pelo Thymeleaf.

## 🏗️ Como Rodar o Projeto
Clone o repositório:

```
git clone [https://github.com/allanflm/notificacao.git](https://github.com/allanflm/notificacao.git)
```

* Desenvolvido por Allan Felipe
