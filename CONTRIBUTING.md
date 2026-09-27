# Contributing to RIAS

Thank you for your interest in contributing to **RIAS (Ryzotek Indigenous Admin Systems)**! We welcome contributions from developers of all skill levels.

---

## Code of Conduct

Please maintain a welcoming, respectful, and constructive environment for all contributors. Treat everyone with empathy and respect.

---

## Development Setup

1. **Fork & Clone**
   ```bash
   git clone https://github.com/your-username/rias.git
   cd rias
   ```

2. **Install Dependencies**
   We use `pnpm` (v12+):
   ```bash
   pnpm install
   ```

3. **Configure Environment**
   ```bash
   cp .env.example .env
   ```
   Generate a random secret for `NEXTAUTH_SECRET`:
   ```bash
   # On macOS / Linux:
   openssl rand -base64 32
   # Or on Windows PowerShell:
   [Convert]::ToBase64String((1..32 | ForEach-Object { Get-Random -Minimum 0 -Maximum 256 }))
   ```

4. **Initialize Database**
   ```bash
   pnpm db:push
   pnpm db:seed
   ```

5. **Start Development Server**
   ```bash
   pnpm dev
   ```
   - Storefront: [http://localhost:3000](http://localhost:3000)
   - Admin Login: [http://localhost:3000/admin/login](http://localhost:3000/admin/login)

---

## Architecture & Code Guidelines

- **Blank Canvas Philosophy**: The storefront must NEVER hardcode content, categories, banners, or layout structure. All content originates dynamically from the database through the Admin Dashboard.
- **Next.js App Router**: Route groups `(store)` for customer-facing pages and `(admin)` for protected dashboard workflows.
- **Type Safety**: Strictly typed with TypeScript. All input validation schemas reside in `src/lib/validators.ts`.
- **CSS Variables & Theming**: Theme colors, fonts, and dark mode are dynamically injected via `src/components/store/theme-provider.tsx` based on `SiteConfig` in the database.
- **Minimal Code Changes**: Fix only what is needed. Do not refactor unrelated code.

---

## Submitting Pull Requests

1. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```
2. Verify that the build succeeds without errors:
   ```bash
   pnpm build
   ```
3. Commit your changes with clear, concise messages.
4. Push your branch and open a Pull Request describing your changes, motivation, and testing steps.

---

## Security Vulnerabilities

If you discover a security vulnerability, please do NOT create a public issue. Instead, report it privately to the maintainers.
