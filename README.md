# LXDAO Developer Guide

This guide outlines the technical stack, branching strategy, development workflow, and coding standards at LXDAO.
[Forum Discussion](https://forum.lxdao.io/t/lxdao-develop-guide-is-out/94)

## Tech Stack

Keep the stack simple. Avoid introducing unnecessary tools or libraries.

### Languages

- **JavaScript / TypeScript**: Full-stack development.
- **Solidity**: Smart contracts.
- **Others**: Project-specific requirements.

### Package Manager

- **[Bun](https://bun.sh/)**: Default package manager. Please migrate existing npm/yarn/pnpm projects to Bun.

### Frontend

- **React Ecosystem**: The core foundation.
- **[Mantine](https://mantine.dev/)**: Recommended UI library. Preferred for its completeness, lightweight nature, and high-quality components (e.g., DatePicker) over MUI/AntDesign/shadcn.
- **Web App**:
  - **React + Vite (SPA)**: Default recommendation.
  - **[Next.js](https://nextjs.org/)**: For applications requiring server-side rendering (SSR) or SEO.
- **[TanStack Query](https://tanstack.com/query/latest)**: Data fetching and state management.
- **[RainbowKit](https://www.rainbowkit.com/)**: Wallet connection.
- **[wagmi](https://wagmi.sh/)** + **[viem](https://viem.sh/)**: The professional standard for Ethereum interactions. Use `wagmi` for React Hooks and `viem` for low-level type-safe interfaces.
- **[Thegraph](https://thegraph.com/)**: For blockchain data

### Backend

- **[tRPC](https://trpc.io/)**: End-to-end type-safe APIs (with Next.js or SPA).
- **[Better Auth](https://better-auth.com/)**: Authentication.
- **[Zod](https://zod.dev/)**: Schema validation.
- **PostgreSQL + [Prisma](https://www.prisma.io/)**: ORM. Prisma's Schema Definition Language (SDL) is preferred over Drizzle's JS abstraction for its clarity and alignment with database modeling.

### Deployment & DevOps (Self-Hosting Best Practice)

We prioritize **Self-Hosting** over managed services (Vercel, Supabase, Heroku, AWS) to ensure transparency, control, and cost-efficiency.

**Recommended Stack:**
- **[Hetzner](https://www.hetzner.com/)**: High-performance, cost-effective dedicated servers.
- **[Coolify](https://coolify.io/)**: Open-source, self-hosted PaaS ("Private Vercel") for CI/CD.
- **Docker**: Containerization.
- **Cloudflare**: CDN, DNS, and Security (Critical for accelerating and protecting EU-based servers).

**Rationale:**
- **Cost**: A single powerful dedicated server is significantly cheaper than usage-based serverless billing at scale.
- **Control**: Eliminates vendor lock-in and "black box" debugging issues.
- **Simplicity**: Consolidates `Next.js`, `tRPC`, `Prisma`, and `PostgreSQL` into a unified environment.

### Tools

- **Scaffolding**: **[create-t3-app](https://create.t3.gg/)** (Recommended for bootstrapping Next.js + tRPC + Prisma projects).
- **Formatting**: Prettier
- **Linting**: ESLint
- **CI/CD**: GitHub Actions
- **Editor**: VSCode, Cursor, or Antigravity
- **AI Coding**: Codex, Claude Code (latest models)
- **Writing**: [Chinese Copywriting Guidelines](https://github.com/sparanoid/chinese-copywriting-guidelines)
- **Smart Contracts**: [DappReader](https://DappReader.com) (Debug contracts like Postman)

## Development

### Environment

- **Local**: Your local development machine.
- **DEV**: Remote testing and preview environment.
- **Production**: Live environment for users.

All three environments (`Local`, `DEV`, `Production`) are required.

### Branching Strategy

- `main`: **Production**. Protected branch reflecting the latest stable release.
- `develop` (or `dev`): **DEV**. Latest integration branch.
- `feature/[name]`: Specific feature implementation.
- `fix/[name]`: Bug fixes.

### Workflow

1.  **Create Issue**: Create or assign a GitHub Issue for the task.
2.  **Branch**: Checkout a new branch from `develop` (or `dev`): `feature/[name]` or `fix/[name]`.
3.  **Develop**: implementations on your local machine.
4.  **Pull Request (Dev)**: Submit a PR to `develop`/`dev`. Verify and test on the `DEV` environment.
5.  **Pull Request (Main)**: Submit a PR from `develop`/`dev` to `main`. Request code review and approval.
6.  **Deploy**: Merging into `main` triggers deployment to Production.

### Code Style

We follow a loose version of the [Airbnb JavaScript Style Guide](https://airbnb.io/javascript/react/).
Install the Prettier plugin and use the default configuration with these overrides:

```json
{
  "singleQuote": true,
  "trailingComma": "all"
}
```

### Commit Messages

Follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification:

- `feat:` New features.
- `chore:` Maintenance (e.g., formatting, dependencies).
- `fix:` Bug fixes.
- `docs:` Documentation updates.

## Coding Music 😁

- [The Midnight](https://www.youtube.com/channel/UC-sM_PLqzgktdUcW2LEKKkQ)

## References

- [How to contribute to React](https://reactjs.org/docs/how-to-contribute.html)
- [Airbnb JavaScript Style Guide](https://airbnb.io/javascript/react/)
- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
