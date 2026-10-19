# Real Estate Listing API

RESTful backend for a Philippine real estate listing and discovery platform, built for ITE 18 (Application Development and Emerging Technologies), Backend Track.

Consumers search and save listings and send inquiries; professionals manage their own listings; administrators verify professionals and moderate listings.

## Tech stack

| Layer | Technology |
| --- | --- |
| Runtime | Node.js 24 LTS |
| Language | TypeScript |
| Framework | NestJS |
| ORM | Prisma 7 |
| Database | PostgreSQL (Neon) |
| Hosting | Render |
| Docs and testing | Swagger, Postman, Vitest |

## Project structure

```
prisma/           Database schema and migrations
src/
  common/         Guards, decorators, exception filter, shared DTOs
  prisma/         Prisma service shared by every module
  auth/           Register, login, JWT
  users/          Own account
  professionals/  Professional profiles and agent directory
  locations/      Region, province, city, barangay (read-only)
  properties/     Listings and search
  property-images/
  favorites/
  inquiries/
  admin/          Account status, verification, moderation
test/             End-to-end tests
docs/             Midterm documentation, ERD, architecture diagram
```

Each feature module will contain `*.module.ts`, `*.controller.ts`, `*.service.ts`, and a `dto/` folder. Empty folders hold a `.gitkeep` until their module is built.

## Getting started

1. Install Node.js 24 LTS.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Copy `.env.example` to `.env` and fill in `DATABASE_URL` and `JWT_SECRET`.
4. Generate the Prisma client and create the tables:
   ```bash
   npx prisma generate
   npx prisma migrate dev --name init
   ```
5. Start the API in watch mode:
   ```bash
   npm run start:dev
   ```

## Scripts

| Command | What it does |
| --- | --- |
| `npm run start:dev` | Run the API with auto-reload |
| `npm run build` | Compile to `dist/` |
| `npm test` | Unit tests |
| `npm run test:e2e` | End-to-end tests |
| `npm run lint` | Lint the code |
| `npm run prisma:migrate` | Create and apply a migration |
| `npm run prisma:studio` | Browse the database in the browser |

## Branching

- `main`: deployed version (Render deploys from it).
- `develop`: integration branch.
- `feature/<name>`: one branch per feature, merged into `develop` through a pull request reviewed by the other backend member.

Never commit `.env`; only `.env.example` belongs in the repository.

## Team

- Khaiel Aldren A. Nasani
- Daryle John Ruta
