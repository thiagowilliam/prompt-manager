# Prompt Manager

Aplicação para gerenciar prompts de IA — crie, edite e delete prompts em um único lugar.

## Tecnologias

| Tecnologia                                           | Versão | Uso                                                |
| ---------------------------------------------------- | ------ | -------------------------------------------------- |
| [Next.js](https://nextjs.org)                        | 16     | Framework React com Server Components e App Router |
| [React](https://react.dev)                           | 19     | Biblioteca de UI                                   |
| [TypeScript](https://www.typescriptlang.org)         | 5      | Tipagem estática                                   |
| [Tailwind CSS](https://tailwindcss.com)              | 4      | Estilização utility-first                          |
| [Prisma](https://www.prisma.io)                      | 7      | ORM para acesso ao banco de dados                  |
| [PostgreSQL](https://www.postgresql.org)             | —      | Banco de dados relacional                          |
| [Radix UI](https://www.radix-ui.com)                 | 1      | Componentes acessíveis sem estilo                  |
| [Lucide React](https://lucide.dev)                   | 1      | Ícones                                             |
| [Jest](https://jestjs.io)                            | 30     | Testes unitários e de componentes                  |
| [Testing Library](https://testing-library.com)       | 16     | Utilitários de teste para React                    |
| [Lefthook](https://github.com/evilmartians/lefthook) | 2      | Git hooks (lint, typecheck e testes no push)       |
| [Prettier](https://prettier.io)                      | 3      | Formatação de código                               |
| [ESLint](https://eslint.org)                         | 9      | Análise estática de código                         |

## Como funciona

A aplicação tem um layout com sidebar lateral e área de conteúdo principal:

- **Sidebar** — lista todos os prompts salvos, buscados direto do banco via React Server Component
- **Área principal** — exibe o prompt selecionado com opções para editar ou deletar; quando nenhum está selecionado, orienta o usuário a escolher um da lista

O modelo `Prompt` no banco possui `id`, `title` (único), `content`, `createdAt` e `updatedAt`.

## Pré-requisitos

- Node.js 20+
- pnpm
- PostgreSQL

## Instalação

```bash
pnpm install
```

Configure a variável de ambiente com a URL do banco:

```bash
# .env
DATABASE_URL="postgresql://user:password@localhost:5432/prompt_manager"
```

Rode as migrations:

```bash
pnpm prisma migrate dev
```

## Scripts

| Comando              | O que faz                            |
| -------------------- | ------------------------------------ |
| `pnpm dev`           | Inicia o servidor de desenvolvimento |
| `pnpm build`         | Gera o build de produção             |
| `pnpm start`         | Inicia o servidor em modo produção   |
| `pnpm test`          | Roda os testes                       |
| `pnpm test:watch`    | Roda os testes em modo watch         |
| `pnpm test:coverage` | Gera relatório de cobertura          |
| `pnpm typecheck`     | Verifica os tipos com TypeScript     |
| `pnpm lint`          | Analisa o código com ESLint          |
| `pnpm format`        | Formata o código com Prettier        |

## Git Hooks (Lefthook)

- **pre-commit** — formata os arquivos staged com Prettier
- **pre-push** — executa `typecheck`, `lint` e `test:coverage` nos arquivos `.ts/.tsx` alterados
