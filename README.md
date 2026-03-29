```
  _   _
 | | | | __ _ _ __   __ _
 | |_| |/ _` | '_ \ / _` |
 |  _  | (_| | | | | (_| |
 |_| |_|\__,_|_| |_|\__,_|
  ____            _     _ _
 / ___|  __ _  ___| |__ (_) | _____
 \___ \ / _` |/ __| '_ \| | |/ / _ \
  ___) | (_| | (__| | | | |   < (_) |
 |____/ \__,_|\___|_| |_|_|_|\_\___/
```

# The Hana Sachiko Company — Website

> Terminal-style interactive website where users type shell commands and chat with an AI character "Hana Sachiko" via GPT-4.

![Preview](public/hanavisu800x600.png)

## Highlights

- **Terminal Interface** — Fully functional command-line UI with shell commands (`help`, `neofetch`, `theme`)
- **AI Chat** — Freeform text triggers GPT-4 streaming with the Hana Sachiko persona
- **3D Effects** — Three.js models and GSAP grid animations
- **Theme System** — Swappable terminal color schemes persisted to localStorage

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Framework | Next.js 14 (App Router) |
| Language | TypeScript |
| Styling | Tailwind CSS |
| AI | OpenAI GPT-4 (Edge Runtime streaming) |
| 3D | Three.js |
| Animations | GSAP |

## Getting Started

```bash
# Install dependencies
npm install

# Start dev server
npm run dev

# Production build
npm run build
```

## How It Works

The site detects whether user input is a valid shell command or freeform text:

- **Shell commands** execute locally via handlers in `src/utils/bin/`
- **Freeform text** is sent to the GPT-4 API as a conversation with Hana Sachiko

## Project Structure

```
src/
├── app/
│   ├── page.tsx              # Main terminal with chat
│   ├── api/chat/route.ts     # Edge runtime GPT-4 streaming
│   ├── me/                   # Content pages
│   ├── mycrew/
│   ├── mycraft/
│   └── dontbeshy/
├── components/
│   ├── chatComponent.tsx     # Dual-purpose input (command / AI chat)
│   ├── layout/Layout.tsx     # GSAP grid animation overlay
│   └── threeEffects/         # Three.js 3D effects
└── utils/
    ├── shellProvider.tsx      # Command history, execution, shell state
    ├── themeProvider.tsx       # Terminal color themes (localStorage)
    └── bin/                   # Command handlers (help, neofetch, theme...)
```

## Configuration

| File | Purpose |
|------|---------|
| `themes.json` | Terminal color schemes |
| `config.json` | Default theme and site settings |

## License

All rights reserved.
