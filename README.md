# Clinic Management System

React + Vite + Tailwind frontend, Node/Express backend, MySQL (MariaDB 10.4+ also works, e.g. XAMPP).

## Setup
1. Start MySQL (XAMPP: start the MySQL module).
2. Backend:
   ```
   cd backend
   cp .env.example .env     # set DB_* and a long random JWT_SECRET
   npm install
   npm run db:init          # creates the database + tables + base data
   npm run db:seed          # role permissions + first Super Admin (ADMIN_USERNAME / ADMIN_PASSWORD in .env)
   npm run dev              # http://localhost:5000
   ```
3. Frontend:
   ```
   cd frontend
   npm install
   npm run dev              # http://localhost:5173 (proxies /api to :5000)
   ```
4. Sign in as the admin, change the password, then create staff under **Staff** (each gets a role).

## Notes
- TV queue screen: `/queue-display` (public, shows ticket numbers only, no patient names).
- Permissions are editable in Settings > Roles & permissions.
- Passwords use `bcryptjs` (bcrypt-compatible, no native build needed on Windows).
- Production: set `NODE_ENV`, a strong `JWT_SECRET`, `CORS_ORIGIN`, serve behind HTTPS, build the frontend with `npm run build`.

## Production (single server)
```
cd frontend && npm run build
cd ../backend && NODE_ENV=production npm start   # serves the API and the built frontend on :5000
```
Reports export to PDF, CSV and real Excel (.xlsx).
