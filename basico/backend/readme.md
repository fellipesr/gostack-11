# O que é Nodejs?

O Nodejs permite utilizar o Javascript no back-end.
O back-end é a camada onde estão as regras de negócios da aplicação. Integração com apis de terceiros, banco de dados, etc...

- Javascript no back-end
  - Não lidamos com eventos do usuário final
  - Rotas e integrações
- Escrita em cima da engine V8, que é o motor do Chrome.
- É uma plataforma, não uma linguagem.

# O que é NPM / YARN?

- Eles são gerenciadores de pacotes.
- Permitem instalar bibliotecas de terceiros dentro do nosso projeto.
- Também permitem fornecer nossas próprias bibliotecas para uso de terceiros.

# Caracteristícas do Nodejs

- Arquitetura Event-loop
  - Baseada em eventos (rotas na maioria das vezes)
  - Call Stack - É uma arquitetura baseada em eventos que trabalha sob uma pilha de eventos, ou seja, funções. O event-loop fica monitorando novos eventos e empilhando-os na call-stack.
    disparadas pelo código.
- O Node é single-thread
  - Utiliza libs c++ no background, como o libuv
  - Background utiliza threads
- Non-blocking I/O
  - Input e output não bloqueante. Ao realizar uma requisição ao Node posso dar a resposta para o cliente sem bloquear a arquitetura.

# Frameworks do Nodejs

- ExpressJS como base

  - Ele não tem uma estrutura fechada
  - Ótimo para iniciantes. Necessita de poucos conceitos para entender seu funcionamento.
  - Pode se utilizar de micro-serviços

- Outros frameworks:
  - AdonisJS
  - NestJS

# Conceitos API Rest

- **Fluxo de requisição e resposta**:
  - Requisição feita por um cliente
  - Resposa retornada através de uma estrutura de dados.
  - Cliente recebe resposta e processa o resultado.
- As rotas utilizam métodos HTTP:

  - GET
  - POST
  - PUT
  - DELETE
  - PATCH
  - Etc...

- Benefícios de API Rest

  - Múltiplos clients (front-end) no mesmo back-end
  - Protocolo de comunicação padronizado
    - Mesma estrutura para web / mobile / API pública
    - Comunicação com serviços externos.

- HTTP Codes
  - São códigos que o backend retorna após uma requisição, é o resultado da requisição:
    - 1xx: Informational
    - 2xx: Success
    - 3xx: Redirection
    - 4xx: Client Error
    - 5xx: Server Error

# Primeiro back-end utilizando Nodejs

- **Dependências**

  - express
  - nodemon
  - uuidv4

- **Curiosidades**
  - Atalho para teclado de emoji **COMMAND + CTRL + SPACE**

# Métodos HTTP

- GET
  - Buscar informações do back-end
- POST
  - Criar uma informação no back-end
- PUT (Altera tudo) / PATCH (altera somente um dado específico)
  - Alterar uma informação no back-end
- Delete
  - Deleta uma informação no back-end

# Tipos de parâmetros

- Query Params:
  - Utilizados principalmente para filtros e paginação
- Route Params:
  - Identificar recursos na hora de atualizar ou deletar
- Request Body:
  - Conteúdo na hora de criar ou editar um recurso

# Middlewares

- Ele é um interceptador de requisições
  - Ele pode:
    - Interromper totalmente uma requisição
    - Alterar dados da requisição
- Quando vou utilizar um middleware?
  - Quando necessitarmos que algum trecho de código seja disparado de forma automática em algumas requisições
