# Sustainability Tracker

A React front-end prototype for logging everyday sustainable actions (recycling, public transport,
planting a tree, saving water, renewable energy) and tracking a sustainability score.

**Live demo:** https://bruce-peters.github.io/sustainability-tracker-app/

What works today (front end only, no backend yet):
- **Home:** sustainability score, a "Log a sustainable action" form (confetti on submit), and a "Show Past
  Actions" list. The score and past actions are placeholder data, and logged actions are not saved yet.
- **Profile** and **About** pages.
- **Settings:** dark-mode toggle and a language picker (held in React context).
- Animated page transitions (Framer Motion) and a mobile dropdown menu.
- **Login, Dashboard, Challenges, Achievements, Feedback** are placeholder pages for now.

## Run it

Prereqs: Node.js 18+ and npm (tested with Node 22.22.0 / npm 10.9.4).

```bash
git clone https://github.com/bruce-peters/sustainability-tracker-app.git
cd sustainability-tracker-app
npm ci
npm run dev        # dev server, open the URL it prints (http://localhost:5173/sustainability-tracker-app/)
```

Other scripts:

| Command | What it does |
|---|---|
| `npm run build` | production build into `dist/` |
| `npm run preview` | serve `dist/` at http://localhost:4173/sustainability-tracker-app/ |
| `npx jest` | run the Jest + Testing Library tests once (`npm test` runs them in watch mode with coverage) |
| `npm run lint` | ESLint |
| `npm run deploy` | build, copy `index.html` to `404.html`, and publish `dist/` to the `gh-pages` branch |

The app is served under `/sustainability-tracker-app/` (Vite `base` and the router `basename`), so open
that path rather than `/`.

## Project structure

```
src/main.jsx                 entry: SettingsProvider + BrowserRouter
src/App.jsx                  layout, applies dark mode
src/constants/index.js       list of pages / routes used by the navbar and router
src/components/              Navbar, AnimatedRoutes, LogForm, SustainabilityScore, PastActions
src/pages/                   one component per route
src/state/                   settings reducer + React context
src/tests/                   Jest tests (LogForm, Profile)
```

Stack: React 18, Vite 5, Tailwind CSS 3, Framer Motion, React Router 6, react-confetti.

## Notes

- GitHub Pages has no SPA fallback, so `npm run deploy` writes `dist/404.html` (a copy of `index.html`).
  Then a refresh or shared link on a page like `/about` loads the app instead of GitHub's 404 page.
- `npm run lint` currently reports style errors (mostly `react/prop-types` and Jest globals in tests).
  They don't affect the build.
