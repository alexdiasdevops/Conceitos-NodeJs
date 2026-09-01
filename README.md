# 🚀 Node.js & TypeScript Financial Transactions API

[![Node.js](https://img.shields.io/badge/Node.js-18.x-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Express](https://img.shields.io/badge/Express.js-4.x-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![Jest](https://img.shields.io/badge/Jest-Testing-C21325?style=for-the-badge&logo=jest&logoColor=white)](https://jestjs.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

> API RESTful desenvolvida com **Node.js** e **TypeScript** focada na gestão de transações financeiras. O projeto aplica os conceitos de **Separation of Concerns (SoC)**, **Service Pattern**, **Repository Pattern** e **DTOs (Data Transfer Objects)**, garantindo tipagem estática robusta, código limpo e testes unitários automatizados.

---

## 📋 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Arquitetura e Conceitos Aplicados](#-arquitetura-e-conceitos-aplicados)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Endpoints da API](#-endpoints-da-api)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Como Executar](#-como-executar)
- [Testes Automatizados](#-testes-automatizados)
- [Licença](#-licença)

---

## 💻 Sobre o Projeto

A aplicação é um serviço backend responsável pelo registro e controle de transações financeiras do tipo **Entrada (`income`)** e **Saída (`outcome`)**. 

Além de armazenar as transações, a API valida a disponibilidade de saldo em tempo real, impedindo operações de saída que excedam o valor total em conta, e fornece um resumo consolidado do balanço financeiro.

### Principais Funcionalidades:
- 🟢 **Criar Transação**: Registra transações com título, valor e tipo (`income` / `outcome`).
- 🔴 **Validação de Saldo**: Impede a criação de transações do tipo `outcome` com valor maior do que o saldo total disponível.
- 📊 **Listar Transações e Balanço**: Retorna a lista completa de transações cadastradas acompanhada de um resumo financeiro (`income` total, `outcome` total e `total` líquido).

---

## 🏗️ Arquitetura e Conceitos Aplicados

O projeto foi construído seguindo princípios de arquitetura limpa e desacoplada:

- **Service Pattern**: Toda a regra de negócio da aplicação (como verificação de saldo insuficiente) fica isolada em *Services*, evitando poluição nas rotas (*Controllers*).
- **Repository Pattern**: Camada responsável por abstrair a persistência e manipulação dos dados das transações.
- **DTOs (Data Transfer Objects)**: Definição clara dos formatos de dados trafegados entre rotas, serviços e repositórios usando interfaces do TypeScript.
- **Imutabilidade e Tipagem**: Uso rigoroso de tipos e interfaces do TypeScript para prevenção de erros em tempo de compilação.

---

## 🛠️ Tecnologias Utilizadas

- **Runtime**: [Node.js](https://nodejs.org/)
- **Linguagem**: [TypeScript](https://www.typescriptlang.org/)
- **Framework Web**: [Express.js](https://expressjs.com/)
- **Testes Unitários**: [Jest](https://jestjs.io/) & [SuperTest](https://github.com/ladjs/supertest)
- **Utilitários**:
  - `uuid` (Geração de IDs únicos universais)
  - `ts-node-dev` (Execução do servidor em modo de desenvolvimento)
  - `ESLint` & `Prettier` (Padronização de código)

---

## 🛣️ Endpoints da API

### 1. Criar Transação
- **Rota**: `POST /transactions`
- **Body da Requisição**:
  ```json
  {
    "title": "Salário Mensal",
    "value": 5000,
    "type": "income"
  }

2. Listar Transações e Balanço

Rota: GET /transactions

Resposta:
{
  "transactions": [
    {
      "id": "a548f3b2-6c1d-4d92-8f1e-3a2b1c0d9e8f",
      "title": "Salário Mensal",
      "value": 5000,
      "type": "income"
    }
  ],
  "balance": {
    "income": 5000,
    "outcome": 0,
    "total": 5000
  }
}

📂 Estrutura do Projeto

src/
├── models/
│   └── Transaction.ts        # Entidade do dado
├── repositories/
│   └── TransactionsRepository.ts # Persistência e cálculos
├── services/
│   └── CreateTransactionService.ts # Regras de negócio
├── routes/
│   ├── index.ts
│   └── transaction.routes.ts # Endpoints
├── app.ts                    # Middlewares e Express
└── server.ts                 # Boot do servidor

⚡ Como Executar
1.Clonar o repositório e acessar a pasta:

git clone [https://github.com/seu-usuario/nome-do-repositorio.git](https://github.com/seu-usuario/nome-do-repositorio.git)
cd nome-do-repositorio

2 Instalar as dependências:

yarn # ou npm install

3 Iniciar o servidor em modo de desenvolvimento:

 yarn dev # ou npm run dev

 🧪 Testes Automatizados
Para executar a suíte de testes unitários com o Jest:

yarn test



📄 Licença
Este projeto está sob a licença MIT.

 
