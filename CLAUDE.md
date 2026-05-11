# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Common Development Commands

- **Start development server**: `npm run dev` (or `pnpm dev` if using pnpm). This runs `next dev`.
- **Build for production**: `npm run build` – runs `next build`.
- **Start production server**: `npm start` – runs `next start` on the built output.
- **Lint**: `npm run lint` – runs `next lint`.
- **Run a single test**: The project currently has no test script; add one to `package.json` if needed, then use `npm test -- <test-file>`.

## High‑Level Architecture

- **Framework**: Next.js 15 (App Router). Entry point is `app/layout.tsx` which defines the root HTML layout and global metadata. Each page lives under `app/` – the main portfolio page is `app/page.tsx`.
- **Component Library**: UI components are organized under `components/` and further under `components/ui/`. Most UI elements are built with Radix UI primitives and Tailwind CSS, with custom wrappers (e.g., `Button`, `SkillBadge`, `ProjectCard`). The `components/ui/` directory provides reusable primitives such as `button.tsx`, `dialog.tsx`, `toast.tsx`, etc.
- **Styling**: Tailwind CSS is the primary styling system (`tailwind.config.ts`). Global styles live in `styles/globals.css` and are imported in `app/layout.tsx`.
- **Utilities**: Shared helper functions are in `lib/utils.ts`.
- **Pages / Sections**: The portfolio is composed of several sections (hero, about, skills, projects, experience, contact) each represented by a component in `components/` and assembled in `app/page.tsx`.
- **Static Assets**: Images and placeholders reside in `public/`.
- **Routing**: No API routes are defined; the site is purely static/SSR.

## Project Structure Overview

```
app/                # Next.js App Router pages and layout
  layout.tsx        # Root layout and metadata
  page.tsx          # Main portfolio page
components/          # Feature components (hero, skills, etc.)
components/ui/     # Reusable UI primitives (button, dialog, toast, …)
lib/                # Utility functions
public/             # Static assets (images, icons)
styles/             # Global CSS (Tailwind imports)
next.config.mjs      # Next.js config (default)
package.json        # Scripts and dependencies
tailwind.config.ts   # Tailwind configuration
tsconfig.json       # TypeScript settings
```

## Development Tips

- Run `npm install` after cloning to install dependencies.
- Use the Tailwind IntelliSense extension in VS Code for class suggestions.
- Component props are strongly typed; refer to their TypeScript definitions for usage.
- The site is designed for Vercel deployment; simply push to a linked Vercel project to trigger a preview.

## Vercel Deployment

- The repository is already Vercel‑ready. Linking the repo in the Vercel dashboard will create preview URLs automatically.
- For production, use the `vercel` CLI: `vercel --prod` after a successful build.

---

*Generated for Claude Code to streamline onboarding and day‑to‑day development.*
