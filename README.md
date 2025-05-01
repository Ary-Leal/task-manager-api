📌 README.md – API de Gerenciamento de Tarefas

# API de Gerenciamento de Tarefas

Esta API permite gerenciar tarefas, incluindo criação, edição, exclusão e autenticação de usuários.

## 🚀 Tecnologias Utilizadas

- **Node.js** – Ambiente de execução JavaScript.
- **Express.js** – Framework para criação do servidor.
- **MongoDB** – Banco de dados NoSQL.
- **Mongoose** – ODM para manipulação do MongoDB.
- **JWT** – Autenticação segura.
- **Joi** – Validação de entrada.
- **Postman** – Ferramenta para testar requisições.

---

## 📦 **Instalação**

Clone este repositório:

```bash
git clone https://github.com/seu-repositorio/task-manager-api
cd task-manager-api
Instale as dependências:

bash
npm install
Crie um arquivo .env e adicione:

env
MONGO_URI=mongodb://localhost:27017/taskmanager
JWT_SECRET=seu_segredo_jwt
🏗️ Rodando o Servidor
Inicie o servidor:

bash
node server.js
Agora sua API estará rodando em http://localhost:5000.

🔄 Rotas da API
📝 Autenticação
Método	Rota	Descrição
POST	/auth/register	Registra um novo usuário.
POST	/auth/login	Faz login e retorna um token JWT.
✅ Tarefas
Método	Rota	Descrição
POST	/tasks	Cria uma nova tarefa. (Necessário JWT)
GET	/tasks	Lista todas as tarefas. (Necessário JWT)
PUT	/tasks/:id	Atualiza uma tarefa. (Necessário JWT)
DELETE	/tasks/:id	Exclui uma tarefa. (Necessário JWT)
🧪 Testando com Postman
1️⃣ Abra o Postman e crie uma nova requisição.

2️⃣ Cadastre um usuário:

Método: POST

URL: http://localhost:5000/auth/register

Body (JSON):

json
{
  "email": "usuario@email.com",
  "password": "senha123"
}
3️⃣ Faça login e obtenha um token JWT:

Método: POST

URL: http://localhost:5000/auth/login

Body (JSON):

json
{
  "email": "usuario@email.com",
  "password": "senha123"
}
Copie o token JWT da resposta.

4️⃣ Crie uma tarefa:

Método: POST

URL: http://localhost:5000/tasks

Headers:

Authorization: Bearer SEU_TOKEN_JWT
Content-Type: application/json
Body (JSON):

json
{
  "title": "Comprar leite",
  "description": "Ir ao mercado e comprar leite",
  "completed": false
}
5️⃣ Consultar todas as tarefas:

Método: GET

URL: http://localhost:5000/tasks

Headers:

Authorization: Bearer SEU_TOKEN_JWT
6️⃣ Editar uma tarefa:

Método: PUT

URL: http://localhost:5000/tasks/:id

Headers:

Authorization: Bearer SEU_TOKEN_JWT
Content-Type: application/json
Body (JSON):

json
{
  "completed": true
}
7️⃣ Deletar uma tarefa:

Método: DELETE

URL: http://localhost:5000/tasks/:id

Headers:

Authorization: Bearer SEU_TOKEN_JWT
🧪 Testes Automatizados com Jest
Instale o Jest:

bash
npm install jest supertest
Crie um arquivo de teste tests/task.test.js:

javascript
const request = require('supertest');
const app = require('../server');

describe('Task API', () => {
    it('Deve criar uma nova tarefa', async () => {
        const response = await request(app)
            .post('/tasks')
            .set('Authorization', 'Bearer SEU_TOKEN_JWT')
            .send({ title: 'Nova tarefa', description: 'Descrição da tarefa' });

        expect(response.status).toBe(201);
        expect(response.body.title).toBe('Nova tarefa');
    });
});
Rode os testes:

bash
npm test
🎯 Conclusão
Agora você tem uma API funcional com autenticação, CRUD de tarefas, testes automatizados e integração com Postman! 🚀🔥