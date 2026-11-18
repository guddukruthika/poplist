# TaskFlow — Setup Guide

## Quick Start

1. **Install dependencies**:
   ```bash
   bun install
   # OR
   npm install
   ```

2. **Set up environment variables**:
   ```bash
   cp .env.example .env
   # Edit .env and change SESSION_SECRET to a random value:
   # openssl rand -hex 64
   ```

3. **Create the database**:
   ```bash
   bun run db:push
   # OR
   npx prisma db push
   ```

4. **Start the dev server**:
   ```bash
   bun run dev
   # OR
   npm run dev
   ```

5. **Open the app** at http://localhost:3000

## First Run

When you open the app for the first time:
1. Click "Get started — it's free"
2. Sign up with your name, email, and a password (min 8 chars)
3. You'll be automatically logged in and see your dashboard
4. Click "New Task" to add your first task
5. Default categories (Personal, Work, Study, Business) are pre-created

## Production Deployment

```bash
# Build for production
bun run build

# Start production server
bun run start
```

For production:
- Set `SESSION_SECRET` to a strong random value
- Set `NODE_ENV=production`
- Set up a proper database backup strategy for `db/custom.db`
- Consider adding rate limiting middleware
- Use HTTPS (the cookies automatically become secure in production)

## Tech Stack

- Next.js 16 (App Router)
- React 19 + TypeScript 5
- Tailwind CSS 4 + shadcn/ui
- Prisma ORM + SQLite
- Zustand + TanStack Query
- Recharts for analytics
- Framer Motion for animations
- @dnd-kit for drag-and-drop

## Security

See `download/security-audit-report.json` for the full security audit.
All passwords are hashed with scrypt + random salt.
Sessions use signed httpOnly cookies with SameSite=lax.

Enjoy TaskFlow!
