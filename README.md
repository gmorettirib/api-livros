# 🌿 API de Livros

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10%2B-2E7D32?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/FastAPI-REST_API-1B5E20?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI" />
  <img src="https://img.shields.io/badge/MySQL%20%2F%20MariaDB-Database-388E3C?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL / MariaDB" />
  <img src="https://img.shields.io/badge/Status-Acadêmico-43A047?style=for-the-badge" alt="Status" />
</p>

> Uma API REST simples e organizada para gerenciamento de um catálogo de livros, desenvolvida com **Python + FastAPI**.

Este projeto foi criado com foco acadêmico para transformar conceitos de back-end em prática. Nele são aplicados fundamentos como **APIs REST, métodos HTTP, operações CRUD, validação de dados, integração com banco de dados e documentação automática de endpoints**.

A aplicação utiliza **MySQL/MariaDB** para persistência dos dados, **SQLAlchemy** como ORM, **Pydantic** para validação e **PyMySQL** como driver de conexão.

---

## 🍃 Funcionalidades

> 🟩 **Objetivo:** oferecer uma API enxuta, didática e fácil de testar.


A API concentra as operações essenciais para administrar o catálogo de livros:

- 🔎 Listar todos os livros;
- 🔍 Consultar um livro pelo ID;
- ➕ Cadastrar novos livros;
- ✏️ Atualizar livros existentes;
- 🗑️ Excluir livros;
- ❤️ Verificar o status da API e da conexão com o banco.

Essas rotas seguem o padrão **CRUD** tradicional:

| Operação | Método HTTP | Função |
|---|---|---|
| Create | `POST` | Criar um registro |
| Read | `GET` | Consultar registros |
| Update | `PUT` | Atualizar um registro |
| Delete | `DELETE` | Excluir um registro |

---

## 🎯 Objetivos do projeto

Durante o desenvolvimento, o projeto explora os seguintes conceitos:

- Desenvolvimento de APIs REST;
- Criação de endpoints com FastAPI;
- Utilização dos métodos HTTP;
- Implementação de operações CRUD;
- Integração entre Python e banco de dados relacional;
- Utilização de ORM com SQLAlchemy;
- Validação de dados com Pydantic;
- Configuração através de variáveis de ambiente;
- Utilização de códigos de status HTTP;
- Documentação automática com Swagger UI;
- Organização modular de aplicações back-end.

---

# 🟢 Tecnologias utilizadas

### Python

Linguagem principal utilizada na construção da aplicação.

### FastAPI

Framework utilizado para estruturar e disponibilizar os endpoints REST.

Além de oferecer uma estrutura simples para criação de endpoints, o FastAPI possui suporte integrado à validação de dados e geração automática de documentação.

### SQLAlchemy

ORM responsável por abstrair e organizar a comunicação entre a aplicação Python e o banco de dados.

### Pydantic

Utilizado para validar e estruturar os dados de entrada e saída da API.

### PyMySQL

Driver que permite a conexão do SQLAlchemy com MySQL/MariaDB.

### Uvicorn

Servidor ASGI utilizado para executar a aplicação FastAPI em ambiente de desenvolvimento.

### MySQL / MariaDB

Banco de dados relacional responsável por armazenar os registros do catálogo.

---

# 🌱 Estrutura do projeto

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

# 🔗 Endpoints

## 📋 Resumo

| Método | Endpoint | Descrição |
|---|---|---|
| `GET`                   | `/livros`      | Lista todos os livros                      |
| `GET`                   | `/livros/{id}` | Busca um livro pelo ID                     |
| `POST`                  | `/livros`      | Cadastra um novo livro                     |
| `PUT`                   | `/livros/{id}` | Atualiza um livro                          |
| `DELETE`                | `/livros/{id}` | Exclui um livro                            |
| `GET`                   | `/health`      | Verifica o funcionamento da API e do banco |

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

# 💚 Health Check

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

# ✅ Códigos HTTP

| Código | Status | Utilização |
|---|---|---|
| `200`                  | OK                    | Requisição realizada com sucesso |
| `201`                  | Created               | Registro criado com sucesso      |
| `204`                  | No Content            | Registro excluído com sucesso    |
| `400`                  | Bad Request           | Requisição inválida              |
| `404`                  | Not Found             | Recurso não encontrado           |
| `422`                  | Unprocessable Entity  | Erro na validação dos dados      |
| `500`                  | Internal Server Error | Erro interno da aplicação        |

---

# 🌿 Banco de dados

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

# ⚙️ Instalação e configuração

## Pré-requisitos

Antes de executar o projeto, tenha instalado:

- Python 3.10 ou superior;
- MySQL ou MariaDB;
- Git;
- Pip.

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

# ▶️ Executando a aplicação

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

# 📗 Documentação da API

O FastAPI gera automaticamente uma interface de documentação da aplicação.

## Swagger UI

Com o servidor em execução, acesse:

```text
http://127.0.0.1:8000/docs

```

Através do Swagger é possível:

- Visualizar os endpoints disponíveis;
- Consultar parâmetros;
- Visualizar os modelos de dados;
- Enviar requisições;
- Analisar as respostas;
- Testar códigos HTTP.

## ReDoc

Também é possível acessar uma documentação alternativa:

```text
http://127.0.0.1:8000/redoc

```

---

# 🧪 Testando os endpoints

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

O fluxo começa quando o cliente envia uma requisição HTTP para um dos endpoints disponíveis.

O FastAPI recebe a requisição e direciona o processamento. Quando há dados no corpo da requisição, o Pydantic realiza a validação antes da execução da lógica.

Quando a operação exige persistência ou consulta, SQLAlchemy e PyMySQL fazem a comunicação com o banco de dados.

Ao final do processo, a API retorna ao cliente uma resposta HTTP adequada à operação realizada.

---

# 🛡️ Boas práticas

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

# 🚀 Próximos passos

Possíveis evoluções para deixar o projeto mais completo:

-  Implementação completa do CRUD;
-  Modelos utilizando SQLAlchemy;
-  Schemas utilizando Pydantic;
-  Tratamento global de erros;
-  Paginação;
-  Pesquisa por título;
-  Pesquisa por autor;
-  Filtros por ano de publicação;
-  Ordenação dos resultados;
-  Autenticação;
-  Controle de usuários;
-  Testes automatizados;
-  Docker;
-  Deploy;
-  Monitoramento;
-  Versionamento da API (`/api/v1`);
-  Expansão da documentação.

---

# 🎓 Contexto acadêmico

Este projeto foi desenvolvido principalmente com finalidade **didática e educacional**.

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

- APIs REST;
- HTTP;
- CRUD;
- Python;
- FastAPI;
- SQL;
- Bancos relacionais;
- SQLAlchemy;
- Pydantic;
- Variáveis de ambiente;
- Documentação de APIs;
- Arquitetura back-end.

---

# 👨‍💻 Autor

Desenvolvido por **Vitor Gonçalves Barros**.

GitHub:

[**@vitorgoncalvesb**](https://github.com/vitorgoncalvesb)

Repositório:

[**api-livros**](https://github.com/vitorgoncalvesb/api-livros)

---

# 📄 Licença

Este projeto foi desenvolvido para fins educacionais.

Caso seja disponibilizado futuramente sob uma licença específica, esta seção poderá ser atualizada com os respectivos termos.

---

## 🌟 Considerações finais

A **API de Livros** funciona como uma base prática para estudar os principais fundamentos presentes em aplicações back-end modernas.

Com **Python, FastAPI, SQLAlchemy e MySQL/MariaDB**, o projeto demonstra o ciclo completo de uma requisição: entrada HTTP, validação, processamento, acesso ao banco e retorno da resposta.

A estrutura também permite evoluções futuras, incluindo autenticação, testes automatizados, paginação, filtros, Docker e deploy.

> 🌱 **Aprender APIs é entender como diferentes aplicações conseguem se comunicar — e transformar dados em funcionalidades reais.**

<p align="center"><strong>🌿 Feito para estudar, testar e evoluir.</strong></p>
