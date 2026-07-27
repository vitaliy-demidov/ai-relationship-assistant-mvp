# Рекомендуемая архитектура

## Минимальный стек

- Web/PWA: TypeScript + Next.js App Router, React, Tailwind/shadcn по необходимости. Один full-stack web-проект проще для MVP, чем отдельные SPA и API.
- Backend: TypeScript в Next.js route handlers/server actions; доменная логика в обычных модулях, не в UI.
- БД: PostgreSQL + Prisma; объектное хранилище S3-compatible для временных архивов, шифрование и TTL.
- Очередь: Redis-compatible queue (BullMQ) только для импорта/AI jobs; синхронный happy path не усложнять.
- Валидация: Zod на границах API и AI-ответа.
- Наблюдаемость: структурированные логи без текста сообщений, метрики длительности/ошибок, request-id.
- AI: provider adapter; первым проверить официальный OpenAI Responses API, затем альтернативный провайдер как опциональный адаптер. Модель, промпт и schema version — конфигурация и audit metadata.

## Языки и движки

TypeScript — основной язык приложения: один типизированный контур от UI до API. SQL — только для миграций/диагностики. PostgreSQL — движок транзакций и фильтрации; Redis — не источник истины, а очередь/кэш. Не добавлять Python, если не появится отдельный ML/ETL use case.

## Слои

`app/` — маршруты и server boundary; `domain/` — сущности, use cases, policies; `adapters/` — Postgres, storage, queue, AI; `workers/` — фоновые jobs; `contracts/` — Zod/OpenAPI; `tests/` — unit/integration/e2e.

## Состояние

URL: фильтры и pagination. Client state: только transient UI. БД: пользователи, импорты, нормализованные данные и drafts. Queue: прогресс и retries. Storage: только raw upload с TTL, если он вообще нужен после разбора.

## AI-практика

Использовать Responses API для серверных reasoning/structured-output workflow; выбирать модель по измерениям качества, стоимости и задержки, не зашивать «самую новую» модель навсегда. На 28 июля 2026 официальные docs рекомендуют семейство GPT-5.6: Sol для сложных задач, Terra для баланса, Luna для массовых недорогих операций; это требует перепроверки перед реализацией. Источник: https://developers.openai.com/api/docs/guides/latest-model и https://developers.openai.com/api/docs/models.

Системные правила: не выводить чувствительные атрибуты, не приписывать намерения как факт, указывать недостаток данных, не генерировать давление/манипуляцию/обман, хранить только нужный результат.
