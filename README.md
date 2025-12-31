# 🚀 API REST - Projeto Base com Node.js

[![Node.js](https://img.shields.io/badge/Node.js-v17.2.3-green)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-v5.2.1-blue)](https://expressjs.com/)
[![MariaDB](https://img.shields.io/badge/MariaDB-v3.4.5-orange)](https://mariadb.org/)
[![License: ISC](https://img.shields.io/badge/License-ISC-yellow.svg)](https://opensource.org/licenses/ISC)

> Projeto base de API REST configurado com as melhores práticas de desenvolvimento, incluindo ESLint, Prettier, Sequelize ORM e containerização com Docker.

## 📋 Índice

- [Sobre o Projeto](#sobre-o-projeto)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Estrutura de Pastas](#estrutura-de-pastas)
- [Pré-requisitos](#pré-requisitos)
- [Instalação](#instalação)
- [Configuração do Banco de Dados](#configuração-do-banco-de-dados)
- [Como Usar](#como-usar)
- [Scripts Disponíveis](#scripts-disponíveis)
- [Migrations](#migrations)
- [Padrão de Código](#padrão-de-código)
- [Contribuindo](#contribuindo)
- [Licença](#licença)

## 🎯 Sobre o Projeto

Este é um projeto template de API REST desenvolvido com Node.js e Express, configurado com todas as ferramentas necessárias para iniciar o desenvolvimento de uma aplicação profissional. O projeto já vem com configurações de linting, formatação de código, ORM e containerização.

### ✨ Funcionalidades

- ✅ API RESTful estruturada com Express
- ✅ Integração com MariaDB via Sequelize ORM
- ✅ Migrations para versionamento do banco de dados
- ✅ ESLint e Prettier configurados (Airbnb Style Guide)
- ✅ Ambiente de desenvolvimento com Nodemon
- ✅ Suporte a variáveis de ambiente (.env)
- ✅ Containerização com Docker
- ✅ Estrutura MVC organizada

## 🛠️ Tecnologias Utilizadas

### Core

- **[Node.js](https://nodejs.org/)** - Ambiente de execução JavaScript
- **[Express.js](https://expressjs.com/)** (v5.2.1) - Framework web minimalista

### Banco de Dados

- **[MariaDB](https://mariadb.org/)** (v3.4.5) - Sistema de gerenciamento de banco de dados
- **[Sequelize](https://sequelize.org/)** (v6.37.7) - ORM para Node.js
- **[Sequelize CLI](https://github.com/sequelize/cli)** (v6.6.3) - Interface de linha de comando

### Qualidade de Código

- **[ESLint](https://eslint.org/)** (v9.39.2) - Linter para identificar padrões problemáticos
- **[Prettier](https://prettier.io/)** (v3.7.4) - Formatador de código
- **[ESLint Config Prettier](https://github.com/prettier/eslint-config-prettier)** (v10.1.8) - Desabilita regras conflitantes
- **[ESLint Plugin Prettier](https://github.com/prettier/eslint-plugin-prettier)** (v5.5.4) - Executa Prettier como regra do ESLint

### Utilitários

- **[dotenv](https://github.com/motdotla/dotenv)** (v17.2.3) - Gerenciamento de variáveis de ambiente
- **[Sucrase](https://sucrase.io/)** (v3.35.1) - Compilador super-rápido para desenvolvimento
- **[Nodemon](https://nodemon.io/)** (v3.1.11) - Monitor de mudanças para reinicialização automática

### Padronização

- **[Globals](https://github.com/sindresorhus/globals)** (v16.5.0) - Variáveis globais do JavaScript

## 📁 Estrutura de Pastas

```
44-PROJETO-API-REST-ESLINT/
│
├── node_modules/          # Dependências do projeto
├── src/                   # Código fonte da aplicação
│   ├── config/           # Arquivos de configuração
│   │   └── database.js   # Configuração do banco de dados
│   │
│   ├── controllers/      # Controladores da aplicação
│   │   └── homeControllers.js
│   │
│   ├── database/         # Estrutura do banco de dados
│   │   ├── migrations/   # Migrations do Sequelize
│   │   │   └── 20251230155347-alunos.js
│   │   └── index.js      # Inicialização do Sequelize
│   │
│   ├── middlewares/      # Middlewares personalizados
│   │
│   ├── models/           # Models do Sequelize
│   │   └── AlunoModels.js
│   │
│   ├── routes/           # Definição das rotas
│   │   └── homeRoutes.js
│   │
│   └── app.js            # Configuração do Express
│
├── .editorconfig         # Configuração do editor
├── .env                  # Variáveis de ambiente (não versionado)
├── .gitignore           # Arquivos ignorados pelo Git
├── .prettierrc          # Configuração do Prettier
├── .sequelizerc.cjs     # Configuração do Sequelize CLI
├── eslint.config.js     # Configuração do ESLint
├── nodemon.json         # Configuração do Nodemon
├── package.json         # Dependências e scripts
├── package-lock.json    # Lock das dependências
├── server.js            # Arquivo principal do servidor
├── SCHEMA_MARIADB_APIREST... # Schema do banco de dados
└── table_api_alunos.sql # Script SQL da tabela
```

## 📦 Pré-requisitos

Antes de começar, certifique-se de ter instalado em sua máquina:

- **Node.js** (versão 14 ou superior)
- **npm** ou **yarn**
- **Docker** e **Docker Compose** (para o banco de dados)
- **Git**

## 🔧 Instalação

### 1. Clone o repositório

```bash
git clone https://github.com/loopesm/44-projeto-api-rest-eslint.git
cd 44-projeto-api-rest-eslint
```

### 2. Instale as dependências

```bash
npm install
```

### 3. Configure as variáveis de ambiente

Crie um arquivo `.env` na raiz do projeto:

```env
# Servidor
PORT=3000

# Banco de Dados
DB_HOST=localhost
DB_PORT=3306
DB_NAME=seu_banco
DB_USER=seu_usuario
DB_PASSWORD=sua_senha
```

## 🐳 Configuração do Banco de Dados

### Usando Docker (Recomendado)

O projeto está configurado para usar MariaDB via Docker. Execute:

```bash
docker run --name mariadb-api \
  -e MYSQL_ROOT_PASSWORD=sua_senha \
  -e MYSQL_DATABASE=seu_banco \
  -p 3306:3306 \
  -d mariadb:latest
```

Ou use o Docker Compose (crie um arquivo `docker-compose.yml`):

```yaml
version: '3.8'
services:
  mariadb:
    image: mariadb:latest
    container_name: mariadb-api
    environment:
      MYSQL_ROOT_PASSWORD: sua_senha
      MYSQL_DATABASE: seu_banco
    ports:
      - '3306:3306'
    volumes:
      - mariadb_data:/var/lib/mysql

volumes:
  mariadb_data:
```

Execute:

```bash
docker-compose up -d
```

### Executar as Migrations

Após configurar o banco de dados, execute as migrations:

```bash
npm run db:migrate
```

## 🚀 Como Usar

### Modo Desenvolvimento

```bash
npm run dev
```

O servidor será iniciado em `http://localhost:3000` (ou a porta configurada no `.env`) com reload automático via Nodemon.

### Modo Produção

```bash
npm start
```

## 📝 Scripts Disponíveis

| Script               | Descrição                                             |
| -------------------- | ----------------------------------------------------- |
| `npm run dev`        | Inicia o servidor em modo desenvolvimento com Nodemon |
| `npm run db:migrate` | Executa as migrations pendentes                       |
| `npm run db:create`  | Cria uma nova migration                               |
| `npm test`           | Exibe mensagem de erro (testes não configurados)      |

## 🗄️ Migrations

### Criar uma nova migration

```bash
npm run db:create -- --name=nome-da-migration
```

### Executar migrations

```bash
npm run db:migrate
```

### Reverter última migration

```bash
npx sequelize db:migrate:undo
```

## 💅 Padrão de Código

Este projeto segue o **Airbnb JavaScript Style Guide** com algumas customizações:

- **ESLint**: Análise estática de código
- **Prettier**: Formatação automática
- **EditorConfig**: Configuração consistente entre editores

### Executar linting manualmente

```bash
npx eslint src/
```

### Formatar código com Prettier

```bash
npx prettier --write "src/**/*.js"
```

## 🤝 Contribuindo

Contribuições são sempre bem-vindas! Siga estas etapas:

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença ISC. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## 📞 Contato

**Moisés Lopes** - Software Developer

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/moises-e-lopes/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/loopesm)

---

## 💼 Outros Projetos

Confira também o **[Contato-Fácil](https://github.com/loopesm/ContatoFacil.git)** - Uma aplicação web completa para gerenciamento de contatos com autenticação, CRUD, interface responsiva e proteção de dados.

---

⭐️ **Se este projeto foi útil para você, considere dar uma estrela!**

**Desenvolvido por Moisés Lopes usando Node.js e Express**
