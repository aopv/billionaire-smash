# Billionaire Smash

Who's more smash-worthy? Vote on billionaires in head-to-head matchups, ranked by Elo.

**Live at [bsmash.aopv.dev](https://bsmash.aopv.dev)**

## Tech Stack

- **Framework**: Next.js 15 + TypeScript
- **Styling**: Tailwind CSS v4
- **Database**: SQLite via Prisma (local), Turso (production)
- **Data**: Forbes 400 API

## Getting Started

```bash
npm install
npx prisma db push
npm run db:seed
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Environment Variables

**`.env`** — production database config

```
TURSO_DATABASE_URL=libsql://your-db.turso.io
TURSO_AUTH_TOKEN=your-token
```

**`.env.local`** — local development overrides

```
TURSO_DATABASE_URL=
TURSO_AUTH_TOKEN=
```

## Project Structure

```
src/
  app/
    page.tsx              # Arena (voting page)
    leaderboard/page.tsx  # Elo leaderboard
    api/
      pair/route.ts       # Random billionaire pair
      vote/route.ts       # Submit vote
      leaderboard/route.ts
      feed/route.ts       # Live feed
      visitors/route.ts   # Visitor counter
      sync/route.ts       # Forbes data sync
  components/
    LiveFeed.tsx          # Scrolling live ticker
    Nav.tsx
    Footer.tsx
  lib/
    prisma.ts             # Prisma client (Turso adapter in prod)
prisma/
  schema.prisma
  seed.ts
```

## Deployment

Deploy to Cloudflare Workers with `npm run deploy` and configure the environment variables as Worker secrets. The app uses Turso as the production database — no filesystem required.

Custom domain: `bsmash.aopv.dev`
