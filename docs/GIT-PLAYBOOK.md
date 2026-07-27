# Git простыми словами

Git — история изменений проекта. `main` — всегда рабочая ветка. Не работать прямо в `main`.

## Ветки

`feat/import-parser`, `fix/tenant-check`, `docs/privacy-policy`, `test/recommendation-contract`. Одна ветка — одна понятная задача. Сначала обновить `main`, затем создать ветку.

## Коммиты

Формат Conventional Commits: `feat: add archive import contract`, `fix: enforce workspace ownership`, `docs: record retention decision`. Один коммит — одна логическая мысль. Не коммитить `.env`, архивы, дампы и секреты.

## PR

PR — просьба проверить ветку и объединить её с `main`. В описании: зачем, что изменено, как проверено, риски приватности, нужны ли миграции. Минимум один reviewer; для security/privacy изменений — обязательный security review. CI должен пройти: format, lint, typecheck, unit/integration tests, dependency/security checks.

## Теги и релизы

SemVer: `v0.1.0` — первый MVP, `v0.1.1` — исправление, `v0.2.0` — совместимое расширение. До `1.0.0` API может меняться, но миграции и breaking changes документировать. Release notes содержат scope, known limitations и rollback plan.
