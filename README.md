# Trinus IA Monorepo

Este é o monorepo para o projeto Trinus IA, que integra um frontend desenvolvido em Flutter e um backend construído com NestJS.

## Estrutura do Projeto

O monorepo é organizado da seguinte forma:

- `apps/`: Contém as aplicações principais do projeto.
  - `trinus-ia-backend/`: Aplicação backend desenvolvida com NestJS.
  - `trinus-ia-frontend/`: Aplicação frontend desenvolvida com Flutter.
- `packages/`: Contém bibliotecas e pacotes de código compartilhado entre as aplicações.
  - `shared-dtos/`: Definições de DTOs (Data Transfer Objects) compartilhadas.
  - `shared-utils/`: Utilitários e funções de uso geral.

## Tecnologias Utilizadas

- **Frontend:** Flutter (para iOS, Android, Web)
- **Backend:** NestJS (Node.js, TypeScript)
- **Banco de Dados:** PostgreSQL
- **ORM:** TypeORM
- **Containerização:** Docker, Docker Compose
- **Versionamento:** Git, GitHub

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

## Como Rodar o Projeto

Detalhes sobre como iniciar o backend, frontend e a infraestrutura serão adicionados nas seções específicas de cada aplicação e na configuração do Docker Compose.

## Contribuição

Instruções para contribuição serão adicionadas posteriormente.

## Licença

Este projeto está licenciado sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.
