# ROYALDATA Ghana — Starter Project

This is a starter project based on the supplied mobile website preview. It includes the front-end demo plus a backend foundation and PostgreSQL schema. It is **not yet a live store**: Datamart API endpoints/credentials and a payment provider account must be verified and configured before real orders can be fulfilled.

## Project structure

- `public/index.html` — current website preview (login-first, sign-up switch, guest browsing, bundle catalogue, demo checkout and tracking).
- `server/src/index.js` — Express API starter with health endpoint and safe placeholder routes.
- `server/src/datamart.js` — integration adapter deliberately left unconfigured until official Datamart API documentation is available.
- `server/sql/schema.sql` — initial PostgreSQL schema for users, bundles, orders, payment transactions, wallet ledger and status history.
- `.env.example` — environment variable template; never commit real secrets.

## Run the static preview

Open `public/index.html` in a browser. The purchase, login, wallet and tracking actions are demonstrations only.

## Run the backend starter

Requires Node.js 20+ and PostgreSQL.

1. In a terminal, enter `server/`.
2. Run `npm install`.
3. Copy `.env.example` to `.env` and fill in your own local database settings. Do not add secrets to GitHub.
4. Create a PostgreSQL database and apply `sql/schema.sql` using your database client.
5. Run `npm run dev`.
6. Visit `http://localhost:3000/api/health`.

The backend intentionally returns `501` for Datamart and checkout integration until the official API specification and payment provider are configured. Do not change these routes to claim success without real provider calls and tests.

## Before live launch

- Obtain permission and official API documentation for the Datamart account/API you are authorised to use.
- Verify endpoint URLs, authentication, product IDs, status rules, timeout behaviour, idempotency support and webhook signatures.
- Choose a Ghana-supported payment provider and implement server-side verification.
- Implement customer authentication, password hashing, sessions, CSRF protections where applicable, rate limits, input validation and account recovery.
- Add wallet ledger transactions with database locking and audit trails; never trust browser-supplied balances.
- Configure HTTPS, database backups, monitoring, production secrets and a live test plan.
- Confirm current supplier prices and network availability. Prices in the HTML are illustrative/sample values from the supplied reference screenshots and must be verified before launch.

## GitHub

Push this project to a **private** GitHub repository while developing. GitHub is source control; deploy the backend to a suitable Node.js host and PostgreSQL to a managed database provider. GitHub Pages is not appropriate for hosting the live commercial checkout system.
