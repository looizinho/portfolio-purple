# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Common Development Commands

Use **pnpm** for package management (the lock file is `pnpm-lock.yaml`). All scripts below work with `npm`, `yarn`, or `pnpm`:

- **Start development server**: `pnpm dev` – runs `next dev` and reloads on file changes.
- **Build for production**: `pnpm build` – runs `next build`.
- **Start production server**: `pnpm start` – runs `next start` on the built output.
- **Lint**: `pnpm lint` – runs `next lint`.

## High‑Level Architecture

- **Framework**: Next.js 15 (App Router). Entry point is `app/layout.tsx` which defines the root HTML layout and global metadata. Main portfolio page is `app/page.tsx`.
- **UI Components**: `components/ui/` contains shadcn/ui primitives (Button, Dialog, Toast, etc.) – add new ones with `npx shadcn-ui@latest add <component>`. Feature components like `ProjectCard`, `SkillBadge`, and `CreativeHero` are in `components/`.
- **Styling**: Tailwind CSS with CSS variables for theming (`tailwind.config.ts`). Global styles are in `app/globals.css`.
- **Animations**: Framer Motion is used for component animations throughout the site.
- **Custom Hooks**: `hooks/` contains utilities like `use-mobile` (responsive breakpoint detection) and `use-toast` (toast notification system).
- **Utilities**: `lib/utils.ts` contains shared helper functions (primarily for class merging via clsx/tailwind-merge).
- **Page Composition**: The portfolio sections (hero, about, skills, projects, experience, contact) are assembled in `app/page.tsx` with floating navigation, scroll progress tracking, and custom mouse following effects.
- **No API routes** – the site is purely client-side rendered with static content.

## Project Structure

```
app/                    # Next.js App Router
  layout.tsx            # Root layout
  page.tsx              # Main portfolio page
  globals.css           # Global styles
components/             # Feature components (CreativeHero, ProjectCard, etc.)
  ui/                   # shadcn/ui primitives
hooks/                  # Custom React hooks (use-mobile, use-toast)
lib/                    # Utilities (utils.ts for class merging)
public/                 # Static assets
components.json         # shadcn/ui configuration
next.config.mjs         # Next.js settings (ESLint/TS errors ignored)
tailwind.config.ts      # Tailwind CSS config with animations
tsconfig.json           # TypeScript configuration
```

## Key Notes

- **Build Configuration**: `next.config.mjs` intentionally disables ESLint and TypeScript build errors. These are still checked during `pnpm lint` but don't block builds.
- **Image Optimization**: Images are unoptimized (next/image optimization is disabled) for simpler asset handling.
- **Adding UI Components**: Use `npx shadcn-ui@latest add <component>` to add shadcn/ui components (they'll be installed in `components/ui/`).
- **Origin**: Built with v0.dev (Vercel's AI component generator) – this context may be relevant for future v0 integrations.

## Deployment

The site is Vercel-ready. Push to a linked Vercel repository to trigger automatic previews and production deployments.
