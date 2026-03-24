# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm install    # Install dependencies
npm run dev    # Start development server
npm run build  # Build for production
npm run lint   # Run ESLint
```

## Architecture

This is a Next.js 14 (App Router) application that presents a terminal-style interactive website for The Hana Sachiko Company - a storytelling studio.

### Core Concept
The site mimics a command-line terminal interface where users can:
1. Type shell commands (help, neofetch, theme, etc.) that execute locally
2. Chat with an AI character "Hana Sachiko" via OpenAI GPT-4

### Key Architectural Layers

**Providers (src/utils/)**
- `shellProvider.tsx`: Manages command history, execution, and shell state via React Context. Commands are dispatched through the `execute()` function which looks up handlers in `src/utils/bin/`
- `themeProvider.tsx`: Manages terminal color themes from `themes.json`, persisted to localStorage

**Command System (src/utils/bin/)**
- Each file exports async functions that serve as terminal commands
- `index.ts` re-exports all commands - add new commands there
- Commands receive `args: string[]` and return `Promise<string>` output
- Special handling: `theme` command receives a callback to update theme state

**Chat Integration**
- `src/components/chatComponent.tsx`: Dual-purpose input - detects if input is a valid command (executes locally) or freeform text (sends to AI)
- `src/app/api/chat/route.ts`: Edge runtime route using OpenAI streaming with the Hana Sachiko persona

**Visual Effects**
- `src/components/layout/Layout.tsx`: GSAP grid animation overlay on page load
- `src/components/threeEffects/`: Three.js effects including 3D models and shader-based image effects

### Pages
All pages share the same terminal layout:
- `/` - Main terminal with chat
- `/me`, `/mycrew`, `/mycraft`, `/dontbeshy` - Content pages with sidebar navigation

### Configuration Files
- `themes.json`: Terminal color schemes (root level)
- `config.json`: Default theme and site settings (root level)
