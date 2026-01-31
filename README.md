# Prayer Warrior Collection — Full App (Code)

This repo is a complete Next.js full-stack app with:
- Storefront + products
- Prayer Room (daily prayers + prompts)
- Journals (simple demo)
- Guided Prayer Journeys
- Stripe Checkout (one-time payments)
- Stripe Webhook -> Orders saved in SQLite (Prisma)
- Admin (password) to view admin data

## Install
```bash
npm i
cp .env.example .env
```

## Database
```bash
npx prisma migrate dev --name init
```

## Run
```bash
npm run dev
```

## Stripe webhook (local)
```bash
stripe listen --forward-to localhost:3000/api/stripe/webhook
```
Copy the `whsec_...` value into `.env` as `STRIPE_WEBHOOK_SECRET`.

## Prayer Warrior Guide (3D + Chat + Voice)
- Page: `/guide`
- Add an avatar model file at: `/public/avatar.glb` (export from Ready Player Me)
- Add OpenAI key in `.env`:
  - `OPENAI_API_KEY`
  - `OPENAI_MODEL` (default: gpt-4o-mini)

### Prisma update (favorites)
Journal entries now support `favorite` (boolean). Run:

```bash
npx prisma migrate dev --name journal_favorite
```

## Saved prayers tools
In `/guide` → Saved Prayers:
- ☆ Favorite / ★ Unfavorite
- 🗑️ Delete
- Export to PDF (uses browser Print → “Save as PDF”)

## Mobile-friendly interactive mode (2D)
This version does **not** require a 3D avatar file. Interaction is:
- Tap her portrait to open the Guide (`/guide`)
- Chat (AI) + Speak (device text-to-speech)
- Save / Favorite / Delete / Export prayers

### Replace placeholders
- Background: replace `public/war-room-bg.svg` with `public/war-room-bg.png` (or keep SVG)
- Portrait: replace `public/her-portrait.svg` with `public/her-portrait.png` (or keep SVG)
Update paths in `src/app/globals.css` and pages if you rename files.
