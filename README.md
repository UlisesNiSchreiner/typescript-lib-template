# typescript-lib-template

A Template for building **TypeScript libraries** :  
✔ ESM + CJS + type definitions  
✔ Tests + Coverage (Vitest)  
✔ CI/CD  
✔ LibFlow (branching model for libraries)  
✔ Manual versioning with standard-version  
✔ Husky + lint-staged + commitlint  
✔ npm publishing

![CI](https://img.shields.io/github/actions/workflow/status/UlisesNiSchreiner/typescript-lib-template/ci.yml?label=CI)
![npm version](https://img.shields.io/npm/v/typescript-lib-template)
![npm downloads](https://img.shields.io/npm/dm/typescript-lib-template)
![coverage](https://img.shields.io/badge/coverage-100%25-brightgreen)
![license](https://img.shields.io/badge/License-MIT-green)
![typescript](https://img.shields.io/badge/TypeScript-5.x-blue)

---

# 🚀 Installation

```bash
npm i typescript-lib-template
```

---

# 📦 Usage

```ts
import { sum } from "typescript-lib-template";

console.log(sum(2, 3)); // 5
```

---

# 🧱 Project Structure

```
.
├── src/                 # Source code (TS)
├── test/                # Tests (Vitest)
├── dist/                # Final build (ESM, CJS, .d.ts)
├── .husky/              # Git hooks (lint + commitlint)
├── .github/workflows/   # CI/CD
└── README.md
```

---

# 🔀 LibFlow — Workflow for Libraries

This project uses **LibFlow**, a GitFlow variant optimized specifically for library development.

### 🌿 Main Branches

- **master** → stable / production branch
- **feature/\*** → new features and fixes
- **release/x.y** → release preparation + RC
- **hotfix/\*** → urgent patches on `master`

### 🔄 Full Flow

1. Create a feature:
   ```bash
   git checkout -b feature/my-feature
   ```
2. Open PR → merge into `master`
3. Start a release:
   ```bash
   git checkout -b release/1.2
   ```
4. Publish **Release Candidates**:
   ```bash
   npm run release:rc
   ```
5. Validate + test RC
6. Merge `release/*` → `master`
7. Publish stable version:
   ```bash
   npm run release:patch   # or :minor / :major
   ```

---

# 🏷 Versioning & Releases

This project uses **standard-version** for controlled, manual versioning.

### 📌 Available Commands

| Action              | Script                        | Result         |
| ------------------- | ----------------------------- | -------------- |
| Patch release       | `npm run release:patch`       | x.y.(z+1)      |
| Minor release       | `npm run release:minor`       | x.(y+1).0      |
| Major release       | `npm run release:major`       | (x+1).0.0      |
| Release candidate   | `npm run release:rc`          | x.y.z-rc.n     |
| Finalize RC (patch) | `npm run release:final:patch` | stable version |
| Finalize RC (minor) | `npm run release:final:minor` | stable version |
| Finalize RC (major) | `npm run release:final:major` | stable version |

Each command generates:

- Updated `CHANGELOG.md`
- Updated version in `package.json`
- Git tag `vX.Y.Z`
- Automatic push
- npm publish (requires `NPM_TOKEN`)

---

# 🧪 Main Scripts

| Script                  | Description                    |
| ----------------------- | ------------------------------ |
| `npm run dev`           | Watch build (tsup)             |
| `npm run build`         | Compile ESM + CJS + types      |
| `npm run test`          | Run tests                      |
| `npm run test:coverage` | Coverage with V8               |
| `npm run typecheck`     | TS check without emitting      |
| `npm run docs`          | Generate Typedoc documentation |

---

# 🛠 First-Time Setup

```bash
npm ci
npm run build
npm run test

# enable Husky
git add .
git commit -m "feat: initial setup"
```

---

# 📘 API

### **`sum(a: number, b: number): number`**

Adds two numbers and validates that both are finite.

---

# 📄 License

MIT © Ulises Schreiner
