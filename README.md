# Lista de Tarefas Full-Stack

Aplicação de gerenciamento de tarefas, construída com **Vue 3** no frontend e **Spring Boot** no backend, utilizando **H2** como banco de dados em memória.

Erro encontrado: O erro “Falha ao carregar tarefas” é causado por uma incompatibilidade de porta entre a configuração do frontend (Vue) e a do backend (Spring Boot).

Analisando os arquivos, a causa do problema é a seguinte:

No backend, o arquivo application.properties foi configurado para executar o servidor na porta 8088.
No frontend, o arquivo tarefaService.js está tentando fazer requisições para a porta 8080.
O navegador tenta contatar localhost:8080, não encontra nenhum serviço respondendo e a requisição falha, acionando a mensagem de erro no bloco catch do seu componente Vue.
Correção
Para corrigir, você deve alinhar a baseURL no arquivo tarefaService.js com a porta definida no seu backend.

Arquivo a ser modificado: frontend/app-tarefas/src/services/tarefaService.js
Próximos Passos:

Altere a linha da baseURL no arquivo tarefaService.js de 8080 para 8088.
Salve o arquivo. O servidor de desenvolvimento do Vue (npm run dev) irá recarregar automaticamente.
Atualize a página no seu navegador (http://localhost:5173). O erro deve desaparecer e a lista de tarefas, populada pela classe DataInitializer, será exibida.

---

## 🚀 Tecnologias Utilizadas

- **Frontend:** Vue 3, Vite, Axios  
- **Backend:** Spring Boot, Spring Data JPA, H2 Database  
- **Outros:** Lombok, Maven, Node.js, npm

---
---

## ⚡ Pré-requisitos

- Java 17 ou superior  
- Node.js 20 ou superior  
- npm 9 ou superior  

---

## 🖥️ Executando o Backend (Spring Boot)

1. Abra o terminal na pasta do backend:
```bash
cd backend

./mvnw spring-boot:run  # Linux/Mac
mvnw.cmd spring-boot:run # Windows
http://localhost:8088/api
GET http://localhost:8088/api/tarefas
Abra o terminal na pasta do frontend:

cd frontend


Instale as dependências:

npm install


Rode o servidor de desenvolvimento:

npm run dev


Abra o navegador na URL indicada pelo Vite (normalmente):

http://localhost:5173/
