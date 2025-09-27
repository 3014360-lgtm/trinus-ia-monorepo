# Trinus IA Monorepo

Este é o monorepo para o projeto Trinus IA, que integra um frontend desenvolvido em Flutter e um backend construído com NestJS.

## Estrutura do Projeto

O monorepo é organizado da seguinte forma:

- `apps/`: Contém as aplicações principais do projeto.
  - `trinus-ia-backend/`: Aplicação backend desenvolvida com NestJS.
  - `trinus-ia-frontend/`: Aplicação frontend desenvolvida com Flutter.
- `packages/`: Contém bibliotecas e pacotes de código compartilhado entre as aplicações.
  - `shared-dtos/`: Definições de DTOs (Data Transfer Objects) compartilhadas (a ser implementado).
  - `shared-utils/`: Utilitários e funções de uso geral (a ser implementado).

## Tecnologias Utilizadas

- **Frontend:** Flutter (para iOS, Android, Web)
- **Backend:** NestJS (Node.js, TypeScript)
- **Banco de Dados:** PostgreSQL
- **ORM:** TypeORM
- **Containerização:** Docker, Docker Compose
- **Versionamento:** Git, GitHub
- **Qualidade de Código:** Husky, lint-staged, Prettier, ESLint
- **CI/CD:** GitHub Actions

## Configuração do Ambiente de Desenvolvimento

Para configurar o ambiente de desenvolvimento, siga os passos abaixo:

1.  **Clone o Repositório:**

    ```bash
    git clone https://github.com/3014360-lgtm/trinus-ia-monorepo.git
    cd trinus-ia-monorepo
    ```

2.  **Instale o Docker e Docker Compose:**
    Certifique-se de ter o Docker e o Docker Compose instalados em sua máquina. Você pode seguir as instruções oficiais em [docs.docker.com](https://docs.docker.com/get-docker/).

3.  **Instale o Flutter SDK:**
    Siga as instruções de instalação do Flutter em [flutter.dev/docs/get-started/install](https://flutter.dev/docs/get-started/install).

4.  **Instale o Node.js e npm/yarn:**
    Recomenda-se usar um gerenciador de versões como `nvm` para Node.js. Instale o Node.js (versão LTS) e o npm ou yarn. Veja as instruções em [nodejs.org](https://nodejs.org/en/download/).

5.  **Instale as Dependências da Raiz do Monorepo:**

    ```bash
    npm install
    ```

6.  **Configuração do Husky (Hooks Git):**
    O Husky já está configurado para executar `lint-staged` antes dos commits. Isso garante que o código esteja formatado e sem erros básicos antes de ser commitado. O script `pre-commit` está em `.husky/pre-commit`.

## Como Rodar o Projeto

### 1. Iniciar o Backend e o Banco de Dados (Docker Compose)

Na raiz do monorepo, execute:

```bash
docker-compose up --build
```

Isso irá:

- Construir a imagem Docker para o backend NestJS.
- Iniciar um container PostgreSQL.
- Iniciar o container do backend NestJS, que se conectará ao PostgreSQL.

O backend estará disponível em `http://localhost:3000`.

### 2. Rodar o Frontend (Flutter)

Após o backend estar em execução, navegue até o diretório do frontend e execute:

```bash
cd apps/trinus-ia-frontend
flutter run
```

Isso iniciará a aplicação Flutter no seu dispositivo ou navegador padrão.

## Configuração de Qualidade de Código

O monorepo utiliza as seguintes ferramentas para garantir a qualidade do código:

- **Prettier:** Para formatação automática de código.
- **ESLint:** Para análise estática de código (apenas para o backend NestJS no momento).
- **Husky e lint-staged:** Para automatizar a execução do Prettier e ESLint antes dos commits.

## Integração Contínua (CI/CD) com GitHub Actions

Os workflows de CI/CD são configurados via GitHub Actions para automatizar o build e teste do backend e frontend. Devido a restrições de permissão do ambiente, você precisará criar esses arquivos manualmente no seu repositório GitHub.

Crie a pasta `.github/workflows` na raiz do seu repositório e adicione os seguintes arquivos:

### `.github/workflows/backend-ci.yml`

```yaml
name: Backend CI

on:
  push:
    branches:
      - main
    paths:
      - 'apps/trinus-ia-backend/**'
  pull_request:
    branches:
      - main
    paths:
      - 'apps/trinus-ia-backend/**'

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '18'

      - name: Install dependencies
        run: npm install
        working-directory: apps/trinus-ia-backend

      - name: Run tests
        run: npm run test
        working-directory: apps/trinus-ia-backend
```

### `.github/workflows/frontend-ci.yml`

```yaml
name: Frontend CI

on:
  push:
    branches:
      - main
    paths:
      - 'apps/trinus-ia-frontend/**'
  pull_request:
    branches:
      - main
    paths:
      - 'apps/trinus-ia-frontend/**'

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Flutter
        uses: subosito/flutter-action@v2
        with:
          flutter-version: '3.x'

      - name: Get dependencies
        run: flutter pub get
        working-directory: apps/trinus-ia-frontend

      - name: Run tests
        run: flutter test
        working-directory: apps/trinus-ia-frontend

      - name: Build Web
        run: flutter build web
        working-directory: apps/trinus-ia-frontend

    # - name: Build Android (requires Android SDK setup)
    #   run: flutter build apk
    #   working-directory: apps/trinus-ia-frontend

    # - name: Build iOS (requires macOS runner and Xcode setup)
    #   run: flutter build ios --no-codesign
    #   working-directory: apps/trinus-ia-frontend
```

## Contribuição

Instruções detalhadas para contribuição serão adicionadas em um arquivo `CONTRIBUTING.md` futuramente.

## Licença

Este projeto está licenciado sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.
