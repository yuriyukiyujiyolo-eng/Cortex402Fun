# CORTEX

> Autonomous machine-to-machine payments on Base. Built on Coinbase's **x402** protocol — the internet's native payment layer for AI.

A cinematic, dark-themed single-page landing for the CORTEX token. Loading sequence, HLS video hero, scroll-driven sections, and a tokenomics breakdown — built with React, Vite, Tailwind, GSAP, Framer Motion, and hls.js.

---

## What is x402?

`HTTP 402 Payment Required` was reserved in the original HTTP spec in 1996 and left unused for nearly three decades. Coinbase's **x402** protocol turns it into a programmable payment rail — letting servers price API calls in stablecoins and letting clients (especially AI agents) pay automatically in a single HTTP roundtrip.

```
01  REQUEST     AI agent sends HTTP request to access a paid API or service.
02  HTTP 402    Server responds with "Payment Required" — amount, token, network.
03  SIGN        Agent evaluates, signs USDC payment with its wallet automatically.
04  SETTLE      Payment settles on Base in milliseconds. Server grants access.
```

CORTEX is the token that powers this flow.

---

## Tokenomics

| Allocation                    | %    | Notes                  |
| ----------------------------- | ---- | ---------------------- |
| Fair Launch (Bonding Curve)   | 60%  | Open to all            |
| Team (Locked 6 months)        | 15%  | Hard timelock          |
| Development Fund              | 15%  | Treasury               |
| Community Rewards             | 10%  | Airdrops & incentives  |

- **Total Supply:** 1,000,000,000 CORTEX
- **Network:** Base
- **Contract:** `0x...TBD` (updated after launch)

---

## Tech Stack

- **React 18** + **TypeScript** + **Vite 5**
- **Tailwind CSS** with custom HSL design tokens
- **GSAP** for entrance animations, marquee, and scroll-pinning
- **Framer Motion** for in-view reveals and word transitions
- **hls.js** for the Mux-hosted HLS background video
- **react-router-dom** for routing
- Fonts: **Inter** (body) + **Instrument Serif** italic (display)

---

## Getting Started

```bash
# install
npm install

# dev (http://localhost:5173)
npm run dev

# production build
npm run build

# preview the build
npm run preview
```

Requires Node 18+.

---

## Project Structure

```
src/
├── main.tsx              # entry, BrowserRouter
├── index.css             # tailwind + custom keyframes & HSL tokens
├── pages/
│   └── Index.tsx         # composes the page
└── components/
    ├── LoadingScreen.tsx # 000→100 counter + rotating words
    ├── Navbar.tsx        # floating pill nav with gradient-ring CTA
    ├── Hero.tsx          # HLS bg video + GSAP entrance + role cycler
    ├── HowItWorks.tsx    # 4-step bento grid (REQUEST / 402 / SIGN / SETTLE)
    ├── Features.tsx      # "Why x402" — horizontal pill rows
    ├── Tokenomics.tsx    # supply card + allocation bars + contract row
    ├── Stats.tsx         # 1B / <1s / 402
    └── Footer.tsx        # flipped HLS bg, GSAP marquee, socials
```

---

## Design System

CSS custom properties (HSL, no `hsl()` wrapper — Tailwind adds it):

```css
--bg:      0 0% 4%;
--surface: 0 0% 8%;
--text:    0 0% 96%;
--muted:   0 0% 53%;
--stroke:  0 0% 12%;
```

**Accent gradient** (`linear-gradient(90deg, #89AACC 0%, #4E85BF 100%)`) is reused on:
- Logo ring
- Animated hover borders (`gradient-border` utility, 6s loop)
- Allocation progress bars
- Loading-screen fill

Forced dark theme — no light-mode toggle.

---

## Customization

- **Brand name / wordmark** — change in [`Hero.tsx`](src/components/Hero.tsx) (`<h1>Cortex</h1>`) and [`Navbar.tsx`](src/components/Navbar.tsx) (the `CX` initials).
- **Background video** — replace the `HLS_URL` constant in [`Hero.tsx`](src/components/Hero.tsx) and [`Footer.tsx`](src/components/Footer.tsx) with your own `.m3u8` source.
- **Token allocations** — edit the `ALLOCATIONS` array in [`Tokenomics.tsx`](src/components/Tokenomics.tsx).
- **Contract address** — replace `0x...TBD` in [`Tokenomics.tsx`](src/components/Tokenomics.tsx) after launch.
- **Email + socials** — update in [`Footer.tsx`](src/components/Footer.tsx).

---

## Deploy

The repo is Vercel-ready out of the box — push to GitHub, import the repo on Vercel, framework is auto-detected as Vite. The `dist/` output is fully static.

```bash
# or with the Vercel CLI
npx vercel
```

---

## License

MIT
