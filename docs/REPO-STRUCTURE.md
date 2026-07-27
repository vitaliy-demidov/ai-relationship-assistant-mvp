# Структура будущего репозитория

```text
ai-relationship-assistant/
├── AGENTS.md
├── README.md
├── LICENSE
├── .env.example
├── apps/web/                 # Next.js PWA и server routes
├── packages/domain/          # use cases, policies, domain types
├── packages/contracts/       # Zod schemas, API contracts
├── packages/adapters/        # db, storage, queue, AI providers
├── workers/                  # import и AI jobs
├── prisma/                   # schema и migrations
├── tests/fixtures/           # только synthetic data
├── docs/                     # product, architecture, runbooks
├── decisions/                # ADR, одна запись на решение
├── scripts/                  # безопасные локальные команды
└── .github/                  # CI templates; без secrets в repo
```

## README должен объяснять новичку

Что делает продукт, что не делает, как запустить локально, какие команды проверить, где лежит архитектура, как создать ветку и как удалить локальные данные.

## AGENTS.md должен фиксировать

Границы приватности, команды install/test/lint/typecheck, правила миграций, запрет реальных архивов и секретов, обязательные проверки PR, правила изменения ADR и changelog. Ближайший AGENTS.md действует для своей папки.

## Минимальные роли агентов

- Product/Research: требования, интервью, acceptance criteria.
- Backend/Privacy: домен, импортер, авторизация, удаление.
- Frontend: PWA, доступность, пустые/ошибочные состояния.
- QA/Security: тесты, threat model, regression.

Не нужны отдельные «агенты Telegram», «growth» или «DevOps» до появления соответствующей задачи. Skills: app-blueprint, code-agent, security-review, test-strategy, app-launch-qa; openai-docs — только при работе с OpenAI API. Plugins не устанавливать на этапе blueprint.
