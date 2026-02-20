# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

A Microsoft Power Apps Code App built with React 19, TypeScript, and Vite. Deployed to the Microsoft Power Platform using the `pac` CLI.

## Commands

```bash
npm run dev       # Start dev server with HMR
npm run build     # Type-check and build to dist/
npm run lint      # Run ESLint
npm run preview   # Preview production build locally
```

### Deploy to Power Apps

```bash
npm run build
pac code push
```

## Power SDK CLI

Initialize a new app:
```bash
pac code init -n <app name> -env <environmentId>
```

Add a data source:
```bash
pac code add-data-source -a <apiId> -c <connectionId>
# With table/dataset (e.g., SQL):
pac code add-data-source -a <apiId> -c <connectionId> -t <tableName> -d <datasetName>
```

When data sources are added, the SDK generates files under `src/Models/` and `src/Services/` for data binding. Read those files before working with data sources. Schema references are in `.power/schemas/`.

## Architecture

- `src/main.tsx` — React entry point; mounts `<App>` in StrictMode
- `src/App.tsx` — Root component
- `vite.config.ts` — Vite config with `react()` and `powerApps()` plugins
- `power.config.json` — Power Apps deployment metadata (appId, environmentId, region)
- TypeScript is configured with strict mode; `noUnusedLocals` and `noUnusedParameters` are enforced
