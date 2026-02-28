# Local setup

## Prerequisites
- Node.js 18+
- npm
- Postgres 13+
- git

## Clone and enter repo
```bash
git clone https://github.com/lockydeadzx/next-prisma-tailwind-ecommerce.git
cd next-prisma-tailwind-ecommerce
```

## Start Postgres (Docker)
```bash
docker run --name apple-postgres -e POSTGRES_PASSWORD=postgres -p 5432:5432 -d postgres:15
```

## Env
Copy examples and adjust:
```bash
cp apps/storefront/.env.example apps/storefront/.env.local
cp apps/admin/.env.example apps/admin/.env.local
```
Main env values (same for both):
- `DATABASE_URL` (same DB for both apps)
- `NEXT_PUBLIC_URL` (`http://localhost:7777`)
- mail SMTP (optional in dev)
- Cloudinary (optional)

Example DB URL:
```bash
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/apple_store?schema=public"
```

## Install deps
```bash
cd apps/storefront && npm install
cd ../admin && npm install
```

## Create DB schema (run once from either app)
```bash
npm run db:push
```

## Run dev servers
Storefront:
```bash
cd apps/storefront
npm run dev
# http://localhost:7777
```

Admin:
```bash
cd ../admin
npm run dev
# http://localhost:8888
```

## Import template
A minimal CSV template lives at `docs/import-template.csv` (recommended columns are listed in the Admin import UI).
