# Тёплый круг — локальный MVP

Безопасный демонстрационный веб-продукт: импорт тестового JSON/CSV архива в браузере, список диалогов, карточка контакта, объяснимая рекомендация и редактируемый черновик. Автоматическая отправка, Telegram/Instagram и внешние AI API отсутствуют.

## Запуск

Требуется Node.js 18+ и Python 3 для простого локального сервера.

```bash
npm test
npm run build
npm run dev
```

Откройте http://localhost:4173. Нажмите «Загрузить демо-данные» или выберите собственный синтетический JSON/CSV. Файл обрабатывается только в памяти вкладки и никуда не отправляется.

JSON — массив объектов с полями `name`, `handle`, `date`, `lastMessage`, `topics`, `messages`, `draft`. CSV — `id,name,handle,date,lastMessage,topics,draft`; темы разделяются символом `|`.

## Cloudflare Pages

Проект статический и не требует backend/секретов. В Cloudflare Pages задайте build command `npm run build`, output directory `dist`, Node.js 18+. Для локальной проверки деплойте только synthetic data. Перед публичным доступом обязательно добавить аутентификацию, CSP/security headers, privacy notice и серверную изоляцию данных.

Проверка авторизации перед публикацией: `npx wrangler whoami`. Если команда показывает аккаунт, можно использовать `npx wrangler pages deploy dist --project-name <имя>`. Если нет — выполните `npx wrangler login` самостоятельно; я не запрашиваю и не храню токены.

## Что остаётся для реального запуска

Серверное хранение и удаление, настоящая auth, tenant authorization, импортёр конкретных архивов, rate limits, security review, юридическая политика, provider adapter для AI, мониторинг и отдельный review перед любым white-label.
