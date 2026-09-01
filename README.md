# 🚀 Node.js & TypeScript Transactions API

[![Node.js](https://img.shields.io/badge/Node.js-14.x-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-4.x-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Express](https://img.shields.io/badge/Express.js-4.x-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![Jest](https://img.shields.io/badge/Jest-Testing-C21325?style=for-the-badge&logo=jest&logoColor=white)](https://jestjs.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

> API RESTful desenvolvida em **Node.js** e **TypeScript** para gerenciamento de transações financeiras (entradas e saídas) e cálculo de balanço consolidado. Projeto desenvolvido como desafio prático do Bootcamp GoStack da Rocketseat.

---

## 📋 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades](#-funcionalidades)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Endpoints da API](#-endpoints-da-api)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Como Executar](#-como-executar)
- [Testes Automatizados](#-testes-automatizados)
- [Licença](#-licença)

---

## 💻 Sobre o Projeto

A aplicação é um serviço backend para armazenamento e controle de transações financeiras. O sistema permite cadastrar entradas (*income*) e saídas (*outcome*), além de listar todas as transações juntamente com o balanço financeiro atualizado em tempo real.

O projeto utiliza conceitos fundamentais do ecossistema Node.js com TypeScript, como **Services** para isolar regras de negócio e **Repositories** para abstrair a manipulação dos dados em memória.

---

## ✨ Funcionalidades

- 📌 **Criar Transação**: Cadastra uma nova transação indicando título, valor e tipo (`income` para entrada ou `outcome` para saída).
- 🛑 **Validação de Saldo**: Impede a criação de transações do tipo `outcome` caso o valor seja superior ao saldo total disponível no balanço.
- 📊 **Listar Transações e Balanço**: Retorna todas as transações cadastradas acompanhadas do resumo do balanço financeiro (`income`, `outcome` e `total`).

---

## 🛠️ Tecnologias Utilizadas

- **Runtime**: [Node.js](https://nodejs.org/)
- **Linguagem**: [TypeScript](https://www.typescriptlang.org/)
- **Framework Web**: [Express.js](https://expressjs.com/)
- **Testes Automatizados**: [Jest](https://jestjs.io/) & [SuperTest](https://github.com/ladjs/supertest)
- **Utilitários**:
  - `uuidv4` (Geração de IDs únicos)
  - `ts-node-dev` (Execução do TypeScript em tempo de desenvolvimento)
  - `ESLint` / `Prettier` (Padronização e formatação do código)

---

## 🛣️ Endpoints da API

### 1. Criar Transação
- **Rota**: `POST /transactions`
- **Body**:
  ```json
  {
    "title": "Salário",
    "value": 3000,
    "type": "income"
  }
  ```
- **Resposta de Erro** (se o saldo for insuficiente para uma saída):
  ```json
  {
    "message": "This outcome exceeds your current balance"
  }
  ```

### 2. Listar Transações e Balanço
- **Rota**: `GET /transactions`
- **Resposta**:
  ```json
  {
    "transactions": [
      {
        "id": "uuid-gerado",
        "title": "Salário",
        "value": 3000,
        "type": "income"
      },
      {
        "id": "uuid-gerado",
        "title": "Pagamento Aluguel",
        "value": 1000,
        "type": "outcome"
      }
    ],
    "balance": {
      "income": 3000,
      "outcome": 1000,
      "total": 2000
    }
  }
  ```

---

## 📂 Estrutura do Projeto

```text
src/
├── models/
│   └── Transaction.ts                 # Modelo de dados da Transação
├── repositories/
│   └── TransactionsRepository.ts      # Repositório de manipulação de dados
├── routes/
│   ├── index.ts                       # Gerenciador principal de rotas
│   └── transaction.routes.ts          # Rotas de transações
├── services/
│   └── CreateTransactionService.ts    # Regra de negócio para criação de transação
├── app.ts                             # Configuração do servidor Express
└── server.ts                          # Inicialização do servidor na porta 3333
```

---

## ⚡ Como Executar

1. Clonar o repositório e entrar no diretório:
   ```bash
   git clone [https://github.com/seu-usuario/nome-do-repositorio.git](https://github.com/seu-usuario/nome-do-repositorio.git)
   cd nome-do-repositorio
   ```

2. Instalar as dependências:
   ```bash
   yarn
   ```

3. Iniciar o servidor em modo de desenvolvimento:
   ```bash
   yarn dev:server
   ```

---

## 🧪 Testes Automatizados

Para executar a suíte de testes unitários e de integração com Jest:

```bash
yarn test
```

---

## 📄 Licença

Este projeto está sob a licença **MIT**.
