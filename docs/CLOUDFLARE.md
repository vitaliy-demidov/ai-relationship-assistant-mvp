# Cloudflare Pages deployment

## Safe preview checklist

1. Run `npm test` and `npm run build`.
2. Confirm `dist/` contains only the built static app.
3. Confirm no `.env`, real archive, token, or personal chat is tracked.
4. Verify `npx wrangler whoami` before deploy.
5. Use synthetic demo data only.

For a Pages project, use build command `npm run build` and output directory `dist`. This MVP has no server-side auth or database, so it is suitable only as a public product demo; it is not ready for real personal data.
