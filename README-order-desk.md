# Dai Bhai Khadya Stores — Order Desk

A full-stack internal sales and dispatch app using Express, SQLite and a responsive browser UI. The initial catalogue is extracted from the existing website into `seed-products.js`; existing photo filenames are reused.

## Included
- Owner and salesman logins with role permissions enforced by the API.
- Searchable product catalogue, categories, optional price, photo URL and SKU.
- Owner-only product add/edit/archive and Excel/CSV import.
- Retailer directory maintained by owner.
- Salesmen create orders and edit their own Waiting orders.
- Owner-only Dispatch and Cancel actions. Orders outside Waiting are locked from editing.
- WhatsApp-ready order text. The user selects a chat/group and presses Send in WhatsApp; the app does not silently post to groups.
- Orders do not automatically deduct stock.

## Run locally
1. Install Node.js 20 or newer.
2. Run `npm install`.
3. Copy `.env.example` to `.env`; set a long unique `JWT_SECRET` and owner credentials.
4. Run `npm start` and open http://localhost:5050.

The owner is created from `ADMIN_EMAIL` and `ADMIN_PASSWORD` on the first start. If no account exists, the login screen offers first-time owner setup. Set `SETUP_KEY` to require a key for that setup. SQLite lives at `data/store.sqlite` by default.

## Deploy
Use a Node host with persistent disk. Set `NODE_ENV=production`, `JWT_SECRET`, `ADMIN_EMAIL`, `ADMIN_PASSWORD`, and `DATA_DIR`. For example mount a persistent disk at `/var/data` and set `DATA_DIR=/var/data`. Never use the development JWT secret in production. For serverless/multiple instances, migrate to PostgreSQL.

## Data notes
The old catalogue contains 135 listed product entries; prices are reference values and must be verified before billing. Product photos use existing repository filenames where possible. Some legacy paths may be missing or mismatched, so check image matches and replace with verified image URLs. Publish only product images you have permission to use.
