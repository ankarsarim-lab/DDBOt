# Contributing to Deriv Bot

## Prerequisites

- **Node.js** 20.x (check with `node --version`)
- **npm** 10.x+ (bundled with Node 20)

## Getting Started

### 1. Clone and Install

```bash
git clone https://github.com/ankarsarim-lab/DDBOt.git
cd DDBOt
npm install
```

This automatically sets up Husky git hooks via the `prepare` script.

### 2. Environment Variables

Copy the example env file and fill in required values:

```bash
cp .env.example .env
```

See `.env.example` for all available configuration options. Most are optional for local development.

### 3. Development Server

```bash
npm run dev
```

The app runs at `http://localhost:5000` by default.

### 4. Build

```bash
npm run build
```

Output goes to `dist/`.

## Code Quality

### Linting

```bash
# ESLint + Prettier
npm run test:lint

# Auto-fix
npm run test:fix
```

### Tests

```bash
# Run all tests
npm test

# With coverage
npm run coverage
```

### Pre-commit Hooks

Husky runs automatically on commit:

- **pre-commit**: `lint-staged` (Prettier + ESLint + Stylelint on staged files)
- **commit-msg**: `commitlint` (enforces [Conventional Commits](https://www.conventionalcommits.org/))

Commit message format: `type(scope): description`

Examples:

- `feat(bot-builder): add new block type`
- `fix(trade-engine): handle reconnection edge case`
- `chore(deps): update dependencies`

## Project Structure

```
src/
  app/           # App root, auth wrapper, core providers
  components/    # Shared UI components
  constants/     # App-wide constants
  external/      # Bot skeleton, trade engine, indicators
  hooks/         # React hooks (offline detection, analytics, etc.)
  pages/         # Route-level page components
  stores/        # MobX stores (root store pattern)
  styles/        # Global SCSS styles
  types/         # TypeScript type definitions
  utils/         # Utility functions
  xml/           # Blockly XML definitions
public/          # Static assets, service worker, PWA manifest
```

## Deployment

Deployments are handled via GitHub Actions:

- **Production**: Push a `production_v*` tag
- **Staging**: Push to `master`
- **Test links**: Automatically generated on PRs

All deployments go to Cloudflare Pages with Vercel DR as backup.
