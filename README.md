# 🚀 Desafio Node.js: Tasks API

<p align="center">
  <img src="https://img.shields.io/badge/node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" />
</p>

## 💻 Sobre o Projeto

Este projeto é uma API robusta para gerenciamento de tarefas (CRUD), desenvolvida como parte do **Desafio 01 da trilha de Node.js da Rocketseat**.

O objetivo principal foi construir uma aplicação utilizando **Node.js puro** (sem frameworks como Express), aprofundando conhecimentos em Streams, Buffers, roteamento nativo, middlewares e persistência de dados em sistema de arquivos (JSON).

---

## ⚙️ Funcionalidades

- [x] **CRUD de Tarefas**:
  - `POST /tasks`: Criação de tarefas com campos automáticos (`id`, `created_at`, `updated_at`, `completed_at`).
  - `GET /tasks`: Listagem de tarefas com suporte a filtros por `title` ou `description`.
  - `PUT /tasks/:id`: Atualização de dados específicos de uma tarefa.
  - `DELETE /tasks/:id`: Remoção de tarefas do banco.
  - `PATCH /tasks/:id/complete`: Marcação de tarefa como concluída ou pendente de forma alternada.
- [x] **Importação via CSV**:
  - Script dedicado para leitura de arquivos `.csv` utilizando streams e a biblioteca `csv-parse`, permitindo o cadastro de milhares de registros de forma eficiente.
- [x] **Persistência de Dados**:
  - Armazenamento local em arquivo `db.json`, garantindo que os dados não sejam perdidos ao reiniciar o servidor.

---

## 🛠 Tecnologias e Conceitos

- **Node.js Nativo**: Utilização dos módulos `http`, `fs`, `crypto`, `path` e `url`.
- **Streams**: Processamento de dados por partes (chunks) para eficiência de memória.
- **ES Modules**: Utilização da sintaxe moderna `import/export`.
- **Regex**: Roteamento dinâmico para captura de parâmetros de URL (`:id`).
- **CSV Handling**: Integração com a lib `csv-parse` para manipulação de arquivos de planilhas.

---

## 📋 Regras de Negócio Implementadas

1. **Validação de Campos**: Nas rotas de criação e atualização, validamos se o `title` e `description` foram enviados.
2. **Validação de ID**: Antes de qualquer operação de `UPDATE`, `DELETE` ou `PATCH`, a API verifica se o `id` informado realmente existe no banco de dados, retornando um erro 404 amigável caso contrário.
3. **Datas Automáticas**:
   - `created_at`: Gerada no momento da criação.
   - `updated_at`: Atualizada em toda modificação de dados.
   - `completed_at`: Gerencia o timestamp apenas quando a tarefa é concluída.

---

## 🚀 Como Executar

### 1. Pré-requisitos
- Node.js (v18.0.0 ou superior)
- npm, yarn ou pnpm

### 2. Instalação
```bash
# Clone o repositório
git clone https://github.com/seu-usuario/node-tasks-api.git

# Entre na pasta
cd node-tasks-api

# Instale as dependências
npm install
```

### 3. Executando a API
```bash
# Inicie o servidor em modo de desenvolvimento
npm run dev
```
O servidor estará rodando em `http://localhost:3333`.

### 4. Importação de CSV
Para importar as tarefas do arquivo `scripts/tasks.csv` em massa:
```bash
# Com o servidor da API já rodando, execute em outro terminal:
npm run import
```

---

## 🛣 Documentação da API

### Request Body (Exemplo para POST/PUT)
```json
{
  "title": "Estudar Node.js",
  "description": "Finalizar o desafio de streams da Rocketseat"
}
```

### Endpoints

| Método | Endpoint | Descrição | Parâmetros |
| :--- | :--- | :--- | :--- |
| `GET` | `/tasks` | Lista tarefas | `?search=valor` (opcional) |
| `POST` | `/tasks` | Cria tarefa | JSON Body |
| `PUT` | `/tasks/:id` | Atualiza tarefa | `:id` na URL + JSON Body |
| `DELETE` | `/tasks/:id` | Remove tarefa | `:id` na URL |
| `PATCH` | `/tasks/:id/complete` | Conclui tarefa | `:id` na URL |

---

## 📂 Estrutura de Pastas

```text
├── db.json              # Banco de dados persistente
├── package.json         # Dependências e scripts
├── scripts/             # Scripts utilitários (CSV Import)
│   ├── import-csv.js
│   └── tasks.csv
└── src/                 # Código fonte
    ├── database.js      # Gerenciamento do banco
    ├── routes.js        # Definição das rotas e handlers
    ├── server.js        # Entry point do servidor
    ├── middlewares/     # Middlewares (JSON parsing)
    └── utils/           # Funções auxiliares (Regex, Query parsing)
```

---

## 👨‍💻 Autor

Desenvolvido por **Bruno Bisogni** durante a jornada no Ignite da Rocketseat.

[![Linkedin Badge](https://img.shields.io/badge/-LinkedIn-blue?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/brunobisogni/)](https://www.linkedin.com/in/brunobisogni/)
