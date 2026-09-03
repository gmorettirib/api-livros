# 📚 API de Livros

API REST desenvolvida em **Python com FastAPI** para gerenciamento de um catálogo de livros.

O projeto foi criado com finalidade acadêmica e tem como objetivo colocar em prática conceitos fundamentais de desenvolvimento back-end, como **APIs REST, métodos HTTP, CRUD, validação de dados, integração com banco de dados e documentação de endpoints**.

A aplicação utiliza **MySQL/MariaDB** como banco de dados, **SQLAlchemy** para comunicação com o banco e **Pydantic** para validação dos dados recebidos pela API.

---

## 🚀 Funcionalidades

A API permite realizar as principais operações de gerenciamento de livros:

* 🔎 Listar todos os livros;
* 🔍 Consultar um livro pelo ID;
* ➕ Cadastrar novos livros;
* ✏️ Atualizar livros existentes;
* 🗑️ Excluir livros;
* ❤️ Verificar o status da API e da conexão com o banco.

Essas operações representam o conceito de **CRUD**:

| Operação | Método HTTP | Função                |
| -------- | ----------- | --------------------- |
| Create   | `POST`      | Criar um registro     |
| Read     | `GET`       | Consultar registros   |
| Update   | `PUT`       | Atualizar um registro |
| Delete   | `DELETE`    | Excluir um registro   |

---

## 🎯 Objetivos do projeto

O projeto foi desenvolvido para praticar:

* Desenvolvimento de APIs REST;
* Criação de endpoints com FastAPI;
* Utilização dos métodos HTTP;
* Implementação de operações CRUD;
* Integração entre Python e banco de dados relacional;
* Utilização de ORM com SQLAlchemy;
* Validação de dados com Pydantic;
* Configuração através de variáveis de ambiente;
* Utilização de códigos de status HTTP;
* Documentação automática com Swagger UI;
* Organização modular de aplicações back-end.

---

# 🛠️ Tecnologias

### Python

Linguagem utilizada no desenvolvimento da aplicação.

### FastAPI

Framework responsável pela criação da API REST.

Além de oferecer uma estrutura simples para criação de endpoints, o FastAPI possui suporte integrado à validação de dados e geração automática de documentação.

### SQLAlchemy

ORM utilizado para realizar a comunicação entre a aplicação Python e o banco de dados.

### Pydantic

Responsável pela validação e estruturação dos dados enviados e recebidos pela API.

### PyMySQL

Driver utilizado para conectar o SQLAlchemy ao MySQL/MariaDB.

### Uvicorn

Servidor ASGI utilizado para executar a aplicação FastAPI.

### MySQL / MariaDB

Banco de dados relacional utilizado para armazenar os registros da aplicação.

---

# 🧩 Estrutura do projeto

```text
api-livros/
│
├── app/
│   ├── __init__.py
│   ├── database.py
│   └── main.py
│
├── database/
│   └── biblioteca_db.sql
│
├── .gitignore
├── README.md
└── requirements.txt
```

### 📁 `app/`

Contém os principais arquivos responsáveis pelo funcionamento da aplicação.

#### `main.py`

Arquivo principal da API.

É responsável pela inicialização do FastAPI e pela definição dos endpoints disponíveis.

#### `database.py`

Responsável pela configuração e criação da conexão com o banco de dados utilizando SQLAlchemy.

As credenciais são obtidas através de variáveis de ambiente.

### 📁 `database/`

Contém arquivos relacionados à estrutura do banco de dados.

#### `biblioteca_db.sql`

Script SQL utilizado para criação da estrutura inicial do banco.

O banco utilizado pelo projeto é:

```text
biblioteca_db
```

### 📄 `requirements.txt`

Contém as dependências necessárias para executar a aplicação.

---

# 🔌 Endpoints

## 📋 Resumo

| Método   | Endpoint       | Descrição                                  |
| -------- | -------------- | ------------------------------------------ |
| `GET`    | `/livros`      | Lista todos os livros                      |
| `GET`    | `/livros/{id}` | Busca um livro pelo ID                     |
| `POST`   | `/livros`      | Cadastra um novo livro                     |
| `PUT`    | `/livros/{id}` | Atualiza um livro                          |
| `DELETE` | `/livros/{id}` | Exclui um livro                            |
| `GET`    | `/health`      | Verifica o funcionamento da API e do banco |

---

## 🔎 Listar livros

```http
GET /livros
```

Retorna todos os livros cadastrados.

### Exemplo de resposta

```json
[
  {
    "id": 1,
    "titulo": "Dom Casmurro",
    "autor": "Machado de Assis",
    "ano_publicacao": 1899
  },
  {
    "id": 2,
    "titulo": "O Hobbit",
    "autor": "J. R. R. Tolkien",
    "ano_publicacao": 1937
  }
]
```

---

## 🔍 Buscar livro por ID

```http
GET /livros/{id}
```

Exemplo:

```http
GET /livros/1
```

### Resposta

```json
{
  "id": 1,
  "titulo": "Dom Casmurro",
  "autor": "Machado de Assis",
  "ano_publicacao": 1899
}
```

Caso o livro não seja encontrado:

```http
404 Not Found
```

---

## ➕ Cadastrar livro

```http
POST /livros
```

### Corpo da requisição

```json
{
  "titulo": "O Pequeno Príncipe",
  "autor": "Antoine de Saint-Exupéry",
  "ano_publicacao": 1943
}
```

### Exemplo de resposta

```json
{
  "id": 3,
  "titulo": "O Pequeno Príncipe",
  "autor": "Antoine de Saint-Exupéry",
  "ano_publicacao": 1943
}
```

Uma criação realizada com sucesso pode retornar:

```http
201 Created
```

---

## ✏️ Atualizar livro

```http
PUT /livros/{id}
```

Exemplo:

```http
PUT /livros/3
```

### Corpo da requisição

```json
{
  "titulo": "O Pequeno Príncipe",
  "autor": "Antoine de Saint-Exupéry",
  "ano_publicacao": 1943
}
```

A API localiza o registro pelo ID informado e atualiza seus dados.

---

## 🗑️ Excluir livro

```http
DELETE /livros/{id}
```

Exemplo:

```http
DELETE /livros/3
```

Após a exclusão ser realizada com sucesso, a API pode retornar:

```http
204 No Content
```

---

# ❤️ Health Check

A API possui uma rota responsável por verificar seu funcionamento e a disponibilidade da conexão com o banco de dados.

```http
GET /health
```

### Resposta esperada

```json
{
  "status": "ok",
  "database": "connected"
}
```

Essa rota pode ser utilizada para identificar rapidamente possíveis problemas de conexão ou disponibilidade da aplicação.

---

# 📋 Códigos HTTP

| Código | Status                | Utilização                       |
| ------ | --------------------- | -------------------------------- |
| `200`  | OK                    | Requisição realizada com sucesso |
| `201`  | Created               | Registro criado com sucesso      |
| `204`  | No Content            | Registro excluído com sucesso    |
| `400`  | Bad Request           | Requisição inválida              |
| `404`  | Not Found             | Recurso não encontrado           |
| `422`  | Unprocessable Entity  | Erro na validação dos dados      |
| `500`  | Internal Server Error | Erro interno da aplicação        |

---

# 🗄️ Banco de dados

O projeto utiliza o banco:

```text
biblioteca_db
```

A comunicação ocorre através da seguinte estrutura:

```text
FastAPI
   │
   ▼
SQLAlchemy
   │
   ▼
PyMySQL
   │
   ▼
MySQL / MariaDB
   │
   ▼
biblioteca_db
```

As credenciais do banco não devem ser inseridas diretamente no código.

Para isso, o projeto utiliza variáveis de ambiente definidas em um arquivo `.env`.

### Exemplo

```env
DB_USER=root
DB_PASSWORD=sua_senha
DB_HOST=localhost
DB_PORT=3306
DB_NAME=biblioteca_db
```

> ⚠️ **Importante:** nunca envie o arquivo `.env` para o GitHub quando ele possuir senhas, tokens ou outras informações sensíveis.

Adicione-o ao `.gitignore`:

```gitignore
.env
```

---

# ⚙️ Instalação

## Pré-requisitos

Antes de executar o projeto, tenha instalado:

* Python 3.10 ou superior;
* MySQL ou MariaDB;
* Git;
* Pip.

---

## 1. Clone o repositório

```bash
git clone https://github.com/vitorgoncalvesb/api-livros.git
```

Entre na pasta:

```bash
cd api-livros
```

---

## 2. Crie um ambiente virtual

### Windows

```bash
python -m venv venv
```

Ative o ambiente:

```bash
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
```

Ative:

```bash
source venv/bin/activate
```

---

## 3. Instale as dependências

```bash
pip install -r requirements.txt
```

---

## 4. Configure o banco de dados

Certifique-se de que o MySQL ou MariaDB esteja em execução.

Utilize o script:

```text
database/biblioteca_db.sql
```

para criar a estrutura inicial do banco.

Depois, configure as credenciais no arquivo `.env`:

```env
DB_USER=root
DB_PASSWORD=sua_senha
DB_HOST=localhost
DB_PORT=3306
DB_NAME=biblioteca_db
```

---

# ▶️ Executando o projeto

Com o ambiente virtual ativado, execute:

```bash
uvicorn app.main:app --reload
```

A API ficará disponível por padrão em:

```text
http://127.0.0.1:8000
```

O parâmetro:

```text
--reload
```

faz com que o servidor seja reiniciado automaticamente sempre que alterações forem realizadas no código durante o desenvolvimento.

---

# 📖 Documentação da API

O FastAPI gera automaticamente uma interface de documentação da aplicação.

## Swagger UI

Com o servidor em execução, acesse:

```text
http://127.0.0.1:8000/docs
```

Através do Swagger é possível:

* Visualizar os endpoints disponíveis;
* Consultar parâmetros;
* Visualizar os modelos de dados;
* Enviar requisições;
* Analisar as respostas;
* Testar códigos HTTP.

## ReDoc

Também é possível acessar uma documentação alternativa:

```text
http://127.0.0.1:8000/redoc
```

---

# 🧪 Testando a API

Uma das formas mais simples de testar os endpoints é através do Swagger UI.

Acesse:

```text
http://127.0.0.1:8000/docs
```

Selecione um endpoint e clique em **Try it out**.

Por exemplo, para cadastrar um livro:

```http
POST /livros
```

Utilize:

```json
{
  "titulo": "1984",
  "autor": "George Orwell",
  "ano_publicacao": 1949
}
```

Depois consulte os registros:

```http
GET /livros
```

Também é possível testar o ciclo completo:

```text
POST → Criar
GET → Consultar
PUT → Atualizar
DELETE → Excluir
```

---

# 🔄 Fluxo da aplicação

De maneira simplificada:

```text
               CLIENTE
                  │
                  ▼
              FastAPI
                  │
          ┌───────┴───────┐
          │               │
          ▼               ▼
      Validação         Endpoints
       Pydantic           HTTP
          │               │
          └───────┬───────┘
                  │
                  ▼
             SQLAlchemy
                  │
                  ▼
               PyMySQL
                  │
                  ▼
          MySQL / MariaDB
                  │
                  ▼
            biblioteca_db
```

O cliente envia uma requisição HTTP para um endpoint da API.

O FastAPI recebe e processa a requisição. Quando existem dados no corpo da requisição, eles podem ser validados através do Pydantic.

Caso seja necessário acessar o banco de dados, a aplicação utiliza SQLAlchemy e PyMySQL para realizar a operação.

Ao final, a API devolve uma resposta HTTP ao cliente.

---

# 🔐 Boas práticas utilizadas

### Variáveis de ambiente

Credenciais e configurações sensíveis são armazenadas fora do código-fonte.

### Validação de dados

Os dados recebidos pela API são validados antes de serem processados.

### Status HTTP

Cada operação utiliza códigos HTTP apropriados para representar seu resultado.

### Separação de responsabilidades

Os arquivos da aplicação são organizados de acordo com suas respectivas responsabilidades.

### Documentação

Os endpoints podem ser consultados e testados através da documentação automática disponibilizada pelo FastAPI.

---

# 📈 Melhorias futuras

Algumas funcionalidades que podem ser adicionadas ao projeto:

* [ ] Implementação completa do CRUD;
* [ ] Modelos utilizando SQLAlchemy;
* [ ] Schemas utilizando Pydantic;
* [ ] Tratamento global de erros;
* [ ] Paginação;
* [ ] Pesquisa por título;
* [ ] Pesquisa por autor;
* [ ] Filtros por ano de publicação;
* [ ] Ordenação dos resultados;
* [ ] Autenticação;
* [ ] Controle de usuários;
* [ ] Testes automatizados;
* [ ] Docker;
* [ ] Deploy;
* [ ] Monitoramento;
* [ ] Versionamento da API (`/api/v1`);
* [ ] Expansão da documentação.

---

# 🎓 Finalidade acadêmica

Este projeto possui finalidade principalmente **didática e educacional**.

A proposta é transformar conceitos teóricos de desenvolvimento back-end em uma aplicação prática, permitindo compreender o funcionamento completo de uma API:

```text
Cliente
   ↓
Requisição HTTP
   ↓
FastAPI
   ↓
Validação
   ↓
Regra da aplicação
   ↓
Banco de dados
   ↓
Resposta HTTP
```

Entre os principais conceitos trabalhados estão:

* APIs REST;
* HTTP;
* CRUD;
* Python;
* FastAPI;
* SQL;
* Bancos relacionais;
* SQLAlchemy;
* Pydantic;
* Variáveis de ambiente;
* Documentação de APIs;
* Arquitetura back-end.

---

# 👨‍💻 Autor

Desenvolvido por **Vitor Gonçalves Barros**.

GitHub:

**[@vitorgoncalvesb](https://github.com/vitorgoncalvesb)**

Repositório:

**[api-livros](https://github.com/vitorgoncalvesb/api-livros)**

---

# 📄 Licença

Este projeto foi desenvolvido para fins educacionais.

Caso seja disponibilizado futuramente sob uma licença específica, esta seção poderá ser atualizada com os respectivos termos.

---

## ⭐ Considerações finais

A **API de Livros** é um projeto voltado ao aprendizado dos principais fundamentos necessários para construção de aplicações back-end modernas.

Utilizando **Python, FastAPI, SQLAlchemy e MySQL/MariaDB**, o projeto demonstra desde o recebimento de uma requisição HTTP até a comunicação com o banco de dados e o retorno de uma resposta para o cliente.

O projeto também serve como base para futuras evoluções, como autenticação, testes automatizados, paginação, filtros, Docker e deploy.

> 📚 **Aprender APIs é entender como diferentes aplicações conseguem se comunicar.**
