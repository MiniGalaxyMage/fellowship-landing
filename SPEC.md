# Spec: Fellowship Landing Page

## Objective
Create a single-page landing for Fellowship — a CLI tool that orchestrates AI coding agents. The page must make developers curious enough to install it. Dark, elegant, technical but approachable.

## Product Context — What Is Fellowship?
Fellowship is a CLI tool for developers who work with AI coding agents (Claude Code, Codex, etc.). It lets you:
- **Define teams of AI agents** in a simple `team.yaml` file (roles, models, behaviors)
- **Auto-generate specs** before every implementation — planning and execution are separate phases
- **Writer-Reviewer pattern** — one agent writes code, another reviews it against the spec
- **Interactive review mode** (`--review`) — human-in-the-loop, see the diff, accept/reject/feedback
- **Scribe** — auto-generates documentation after each run
- **Built-in memory** — learnings and gotchas persist across runs (RAM/Disk model)
- **Works with any repo** — `fellowship adopt` on existing projects

**Install command:** `npm install -g fellowship-cli`
**GitHub:** `https://github.com/MiniGalaxyMage/fellowship`

## Design Direction

### Color Palette (from logo V3c — dark mode)
- **Background:** Dark navy #0f1729 to #1a1f35 gradient
- **Primary accent:** Purple/indigo #7c3aed to #a855f7
- **Secondary accent:** Cyan/green terminal glow #2dd4bf / #34d399
- **Text primary:** White #f8fafc
- **Text secondary:** Slate #94a3b8
- **Code blocks:** Slightly lighter dark #1e293b with purple border-left
- **Cards:** Glass morphism effect — semi-transparent backgrounds with subtle blur

### Typography
- Headings: Inter or similar geometric sans-serif, bold
- Body: Inter, regular weight
- Code: JetBrains Mono or Fira Code (monospace)

### Aesthetic
- **Dark tech aesthetic** matching the wizard hat logo
- Subtle particle/grid background animation (very subtle, not distracting)
- Code blocks with syntax highlighting look real, not decorative
- Terminal-style elements ($ prefix, blinking cursor) for commands
- Glow effects on CTAs matching the cyan from the logo

## Page Structure

### 1. Hero Section
- **Logo:** fellowship-logo-v3c.png centered or left-aligned
- **Headline:** "Your AI Agents. One Team. One Command." (or similar — make developers feel the power)
- **Subheadline:** "Fellowship orchestrates AI coding agents with specs, reviews, and memory — so you ship better code, faster."
- **Primary CTA:** A terminal-style box showing:
  ```
  $ npm install -g fellowship-cli
  ```
  With a copy button. This IS the CTA — no signup, no form. Just install.
- **Secondary CTA:** "View on GitHub →" linking to the repo

### 2. The Pitch (Problem → Solution) — keep it SHORT
- 3 short pain points developers recognize:
  - "AI agents write code without context"
  - "No spec means no quality control"
  - "Every run starts from zero — no memory"
- Then: "Fellowship fixes this." → brief transition to features

### 3. Features — 3 key pillars with small visuals/icons
1. **Spec-First Runs** — "Every task starts with a plan. Fellowship auto-generates a spec from your codebase context before writing a single line."
2. **Writer-Reviewer** — "One agent writes, another reviews. Automated quality gates with human override when you want it."
3. **Persistent Memory** — "Learnings, gotchas, architecture decisions — they persist across runs. Your agents get smarter over time."

Each feature should have a small code snippet or terminal output example that feels real.

### 4. How It Works — 3 steps
```
1. fellowship init       → Set up your team
2. fellowship run "task" → Agent writes + reviewer checks
3. git push              → Ship it
```
Show this as a terminal mockup with subtle animation (typing effect or step-by-step reveal on scroll).

### 5. Quick Demo Snippet
A realistic terminal session showing Fellowship in action. Something like:
```
$ fellowship run "add user authentication with JWT"

📋 Generating spec from codebase context...
✅ Spec: 001-jwt-auth.md (12 acceptance criteria)
🤖 Writer (claude-sonnet) implementing...
🔍 Reviewer checking against spec...
✅ All criteria met. 4 files changed, +187/-3
📝 Scribe updated CHANGELOG.md
🚀 Ready to push!
```

### 6. Install + GitHub
- Repeat the install command
- GitHub stars badge
- "MIT Licensed. Built with ❤️ by developers, for developers."

### NO:
- No pricing section (it's free/open source)
- No testimonials (too early)
- No email signup
- No footer with 50 links
- Keep it ONE scroll. Minimal. Curiosity-driven.

## Technical Requirements

### Stack
- **Astro** or plain HTML/CSS/JS — lightweight, fast, SSG
- If using a framework, prefer Astro (fast, minimal JS)
- Tailwind CSS for styling
- No heavy frameworks (React overkill for a landing)

### Assets
- `logo.png` already in project root
- All images/icons via inline SVGs or CSS — no external dependencies

### Deployment
- Must work with Cloudflare Pages (`wrangler pages deploy dist`)
- Output: static files in `dist/`

### Performance
- Total page < 500KB
- First contentful paint < 1.5s
- No JavaScript required for content (progressive enhancement only)
- Lazy load any animations below fold

## Files to Create
```
fellowship-landing/
├── src/
│   ├── index.html (or index.astro)
│   ├── styles/
│   │   └── main.css
│   └── assets/
│       └── logo.png
├── dist/           (build output)
├── package.json
├── tailwind.config.js
└── README.md
```

## Acceptance Criteria
- [ ] Dark theme matching V3c logo aesthetic
- [ ] Hero with logo, headline, install command (copy button)
- [ ] 3 feature cards with code snippets
- [ ] Terminal mockup showing fellowship in action
- [ ] How it works section (3 steps)
- [ ] Mobile responsive
- [ ] < 500KB total
- [ ] Builds to static `dist/` folder
- [ ] `npm run build` works
- [ ] GitHub link present
- [ ] Logo displayed correctly
- [ ] No broken links
