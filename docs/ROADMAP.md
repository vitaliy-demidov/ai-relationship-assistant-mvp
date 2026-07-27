# Дорожная карта

## Phase 0 — Research

Проверить форматы архивов и право обработки, провести 5–8 интервью, собрать синтетические примеры, определить язык и тон. Выход: подтверждённый MVP brief и список рисков.

## Phase 1 — Contracts before UI

Схемы импорта, нормализованного сообщения, recommendation и draft; threat model; ADR; локальный synthetic fixture. Выход: контракты, которые можно тестировать без AI.

## Phase 2 — Vertical slice

Один формат → один workspace → список → карточка → объяснение → draft. Сначала фейковый provider, затем реальный provider behind adapter. Выход: локальный end-to-end сценарий.

## Phase 3 — MVP hardening

Auth, ownership, deletion, limits, queue retries, observability, accessibility, privacy review, backup/restore test. Выход: закрытый тест на обезличенных данных.

## Phase 4 — Personal beta

Небольшая группа пользователей, измерение полезности рекомендаций, ошибок импорта, времени до первого draft и доли ручного редактирования. Не добавлять интеграции по просьбе одного пользователя.

## Phase 5 — White-label discovery

Только после подтверждения личного сценария: интервью с 2–3 клубами, tenant policies, branding, admin boundaries, consent model, агрегаты. Выход: отдельный white-label PRD и security review.

## Phase 6 — White-label beta

Workspace configuration, invitation/roles, per-tenant limits, audit/export/deletion, branded PWA, operator dashboard без доступа к приватному содержимому по умолчанию.
