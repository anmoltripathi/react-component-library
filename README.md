# react-component-library

**Demo app** for a React component library. This Vite + React project is the playground where you render, iterate on, and smoke-test components under real browser conditions—not the published package itself (that would be built and shipped separately).

Right now `src/App.tsx` is still the stock Vite welcome screen (counter, hero, doc links). As you add library pieces, compose them here or split routes/sections so the demo stays easy to browse.

## Stack

- [React](https://react.dev/) 19
- [Vite](https://vite.dev/) 8 with [`@vitejs/plugin-react`](https://github/vitejs/vite-plugin-react)
- TypeScript (project refs: `tsconfig.app.json`, `tsconfig.node.json`)
- [ESLint](https://eslint.org/) 10 with [`typescript-eslint`](https://typescript-eslint.io/) and React hooks / refresh plugins (`eslint.config.js`)

## Prerequisites

- Node.js (LTS recommended)
- npm (lockfile is `package-lock.json`)

## Scripts

| Command           | Description                                     |
|-------------------|-------------------------------------------------|
| `npm run dev`     | Start the demo dev server with HMR              |
| `npm run build`   | Type-check (`tsc -b`) then production build     |
| `npm run preview` | Serve `dist/` (check the demo build locally)    |
| `npm run lint`    | Run ESLint                                      |

## Project layout

```
index.html              # Demo entry (loads /src/main.tsx)
public/                 # Static assets for the demo
src/
  main.tsx              # React root
  App.tsx               # Demo shell — compose/showcase components here
  App.css, index.css    # Global / demo styling
  assets/               # Demo images and similar
vite.config.ts
eslint.config.js
```

Treat **`src/App.tsx` (and future demo-only pages)** as throwaway glue. Put reusable UI in something like **`src/components/`** or **`src/lib/`** so it stays separable from the demo.

## Run the demo locally

```bash
npm install
npm run dev
```

Edit components and the demo; Vite applies hot updates in the browser.

## Demo build

```bash
npm run build
npm run preview
```

Artifacts land in **`dist/`** — that is the built **demo site**, not an npm-ready library bundle.

## Shipping a consumable library

Publishing is not wired up yet. When you’re ready: expose components from an entry module, add types, and use Vite [library mode](https://vite.dev/guide/build.html#library-mode) or a bundler like [tsup](https://github.com/egoist/tsup) so consumers get a proper package; keep this Vite app as the **demo** or move it to a `examples/` / `docs/` app if you split the repo.
