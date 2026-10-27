# MOMO Workspace — Playful Motion SaaS Dashboard

> Custom portfolio design specification | Version 1.0 | 2026-10-27
> Language: Korean-first UI with optional English headings. Theme: Light.
> Mood: clean, playful, friendly, animated, but still a usable professional dashboard.

## 0. Purpose

Build an original, responsive **creative-project and content workflow SaaS dashboard** named **MOMO Workspace**. It should feel like a cheerful personal studio, rather than a rigid ERP/admin console. A small original illustrated mascot guides the user; cards, charts, filters, scheduling, and task management remain immediately understandable.

The name, copy, metrics and illustrations in this document are **original project proposals**, not a representation of any existing company or live data. Mock datasets must be labeled as sample data in a portfolio demo.

### Visual references (inspiration, not a clone)

- Hatch (playful pastel palette, hand-drawn accents, character illustration): https://styles.refero.design/style/e1afed53-6854-40dd-8157-dfc1dd3505f0
- Seline Analytics (sober data hierarchy, clean charts, warm surfaces): https://styles.refero.design/style/7967c6d9-e50c-42b5-b4d1-74003ba41781
- LottieFiles (motion-first illustrations on restrained UI): https://styles.refero.design/style/a80507cb-afda-46dd-a2b9-ba91f3a78e78
- ClickUp (compact productivity controls, pills and status): https://styles.refero.design/style/efcb73cb-b84a-4ae7-9a2b-e1116f79f130

These Refero-generated style documents are reference captures rather than official brand guidelines. Create an original implementation, and do not copy reference logos, brand mascots or artwork.

## 1. Design principles

1. **Structure before decoration.** Keep charts, tasks and filters aligned on a stable grid.
2. **One playful focal point per region.** Do not place mascots on every card.
3. **Motion communicates state.** Animate progress, completion, transitions and feedback—not everything at once.
4. **Pastels for grouping; dark text for reading.** Never use low-contrast pastel-on-white text.
5. **Useful dashboard, not a fake landing page.** Filters, menus, task actions and navigation must work in the portfolio demo.

## 2. Color system

| Token | Hex | Role |
|---|---|---|
| `--bg-canvas` | `#F7F6F2` | warm off-white page canvas |
| `--bg-card` | `#FFFFFF` | primary dashboard card |
| `--bg-soft` | `#F1F4F1` | nested panels and quiet fields |
| `--text-primary` | `#20292A` | main text / data values |
| `--text-secondary` | `#667377` | secondary labels |
| `--border-soft` | `#E7EAE6` | hairline borders |
| `--action-dark` | `#235E4E` | strong text links, focus and active states |
| `--action-mint` | `#A8E9D1` | main filled button with dark text |
| `--accent-lavender` | `#CEC6FA` | calendar and progress groups |
| `--accent-peach` | `#FFD9C5` | reminders / scheduled events |
| `--accent-butter` | `#FFEDB4` | milestones / celebration |
| `--accent-blue` | `#CBE5F7` | insights / analytics illustration |
| `--error` | `#AD3B3B` | error text on a pale error surface |
| `--success` | `#27694F` | positive feedback |

Palette rule: Backgrounds 70%, white cards 20%, pastels and active accents 10% is a visual starting guideline, not a hard-coded calculation. Reserve strong saturation for important actions and chart highlights.

## 3. Typography

### Recommended default: LINE Seed Sans KR + Pretendard Variable
- Korean headings (20–34px; 600–700): **LINE Seed Sans KR**. Friendly geometry without childish letterforms.
- Korean UI / tables / filters / chart labels (13–16px; 400–600): **Pretendard Variable**.
- English brand display only (24–40px; 500–700, optional): **Fredoka**. Never force Fredoka for Korean glyphs; its Korean rendering depends on a separate fallback font.
- Numbers / tabular statistics (28–40px; 600–700): **Plus Jakarta Sans** or Pretendard with `font-variant-numeric: tabular-nums`.

An even simpler production alternative: use Pretendard Variable for the entire application, with 700-weight headlines and rounder illustrations to carry the playful personality.

Type scale: page greeting 32/40; section title 20/28; card title 16/24; body 14/22; caption 12/18; KPI 32/38; buttons 14/20. Avoid overly decorative fonts in tables, dates or charts.

Official references:
- LINE Seed: https://seed.line.me/ ; license information: https://github.com/line/seed
- Pretendard: https://github.com/orioncactus/pretendard
- Fredoka: https://github.com/google/fonts/blob/main/ofl/fredoka/METADATA.pb
- Plus Jakarta Sans: https://github.com/tokotype/PlusJakartaSans

## 4. Grid, radii and density

- Content max width: 1520px; generous 24–32px page padding on desktop.
- Sidebar width: 224px expanded, 76px icon-only collapsed. Main app header: 72px.
- Desktop cards: 20px radius, 1px `--border-soft` border, very soft shadow only where needed.
- Small inputs/buttons: 12px radius; tags/chips: 999px radius.
- 8px spacing rhythm: 8/12/16/20/24/32/40.
- Card padding: 20–28px. Minimum interactive target: ~44x44px when feasible.
- Use an asymmetric **bento dashboard** with predictable underlying grid lines. Do not intentionally misalign table rows and chart axes.
- Chart ink and axes stay quiet; colored fills / marker points carry personality.

## 5. Desktop overview composition (1440px reference)

```
┌────────────────┬───────────────────────────────────────────────────────┐
│                │ TOP: Search • Notifications • Date • User             │
│  MOMO          ├───────────────────────────────────────────────────────┤
│  WORKSPACE     │ Greeting + friendly mascot       | Week achievement   │
│                ├────────────┬────────────┬────────────┬─────────────────┤
│  Overview      │ Projects   │ Completed  │ Scheduled  │ This week's KPI │
│  Projects      ├──────────────────────────┬────────────────────────────┤
│  Calendar      │ Today's priorities      │ Progress / activity chart  │
│  Analytics     ├──────────────────────────┼────────────────────────────┤
│  Assets        │ Mini content calendar    │ Recent projects + assets   │
│  Settings      └──────────────────────────┴────────────────────────────┘
└────────────────────────────────────────────────────────────────────────┘
```

### Modules and interactions

**A. Greeting / character panel**
- Korean copy: `좋은 아침이에요! 오늘도 한 걸음씩 🌱`
- Original 2D mascot, about 96–140px on desktop, gently reacting to dashboard state.
- Optional floating star, seed, leaf or pencil. Avoid reusing the Hatch or Duolingo mascot.
- Highlight one relevant action: `오늘의 작업 시작하기`.

**B. Four KPI cards**
- Ongoing projects, completed tasks, scheduled contents, weekly progress.
- One prominent number per card; one concise status line. Hover slightly raises the card.
- Numbers animate once when revealed; never continuously change in place.

**C. Today's priorities**
- Three to five prioritized task rows with checkboxes, due date and project tag.
- On completion: checkmark stroke animation → card gently collapses / rearranges → one brief particle pop.
- Provide undo and keyboard access. Completion state must persist in localStorage in the demo.

**D. Weekly progress / insights**
- Clear line or rounded-bar chart with axis labels and a visible legend.
- On range selection, interpolate the series; tooltip must reveal exact values.
- Use a small mascot or celebratory illustration only in an empty/goal-reached state, not behind plot labels.

**E. Mini content calendar**
- Week/month toggle; colored project tags; one or more draggable scheduled items if implementation allows it.
- Clicking an event opens a side sheet with details; preserve original placement on cancel.

**F. Recent projects and assets**
- 2–4 project cards with miniature branded thumbnails, progress bar and last update.
- Avoid fake brand partnerships; use custom demo branding / user-owned portfolio assets.

## 6. Motion design — functional, not constantly restless

| Trigger | Suggested treatment | Duration | Implementation idea |
|---|---|---|---|
| Initial page entry | Cards fade and move up 8–14px in stagger | 300–550ms | CSS or GSAP |
| KPI enters viewport | Counter increases from 0 to sample value, once | 700–900ms | JS counter |
| Hover on bento card | `translateY(-3px)`, very soft lift | 180–240ms | CSS transform |
| Checkbox completion | SVG tick draw, tiny confetti, row transition | 350–650ms | SVG + CSS / GSAP |
| Chart filters change | Series morph or crossfade | 400–650ms | chart library |
| Calendar item selected | Side panel slides in 12–20px and fades | 220–350ms | CSS / Vue transition |
| Goal reached | Mascot celebrates exactly once | 800–1200ms | lightweight Lottie / Rive |
| Empty state | Small gentle breathing/float | ≤2–3s loop; rare | Lottie / CSS |

Motion rules:
- A screen may show many interactions but should not run many simultaneous idle loops.
- Prefer `transform` and `opacity` to top/left layout animation.
- Short easing: `cubic-bezier(.22,1,.36,1)`; no bounce on dense table data.
- Keep hover-only visual cues supplemented by focus states on keyboard.
- Respect reduced-motion preferences: disable parallax, entrance staggers, looping mascot motion and counters when `prefers-reduced-motion: reduce`.
- Never obscure exact metrics; keep tooltips usable during chart transitions.

## 7. Interaction states

For every major component provide: Default, Hover, Active/Selected, Focus-visible, Disabled, Loading, Empty and Error when applicable.

- **Loading:** static/soft skeleton with accessible status text; no frenetic shimmer.
- **Empty:** original cheerful illustration plus a clear CTA.
- **Error:** message explaining what failed, retry action and text contrast.
- **Toast:** small bottom-right feedback with 4–6 sec visibility and manual dismiss; keep severe errors persistent.
- **Forms:** real validation and inline error explanations; do not use color as the only status signal.

## 8. Responsive behavior

- **≥1280px:** expanded sidebar, 12-column card grid and full overview.
- **768–1279px:** compact sidebar, two-column cards, tighter padding.
- **<768px:** hide persistent sidebar, use top header and accessible bottom navigation/drawer; one-column cards, first-show tasks and recent activity, then charts and calendar.
- All charts support horizontal/vertical resizing without clipped legends or labels.
- Place larger charts into dedicated sections rather than shrinking them into unreadable thumbnails.

## 9. Suggested stack

The spec works with either of these implementation choices:

**Vue 3 portfolio approach**
- Vue 3 + Vite + CSS/SCSS variables + component-based architecture.
- GSAP for page entry / section transitions; CSS for hovers.
- Chart.js or Apache ECharts for responsive charts; choose ONE.
- Optional Lottie or Rive player only for a small original mascot animation.
- LocalStorage for demo interactions. Backend / authentication not required for prototype.

**Vanilla web approach**
- HTML + SCSS + modern JavaScript + GSAP + Chart.js.
- Functional filters / selection / task completion, with simple local persistence.

Accessibility: semantic navigation, form labels, keyboard-accessible controls, accessible feedback regions and WCAG-appropriate text contrast. Source for reduced-motion behavior: https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/%40media/prefers-reduced-motion

## 10. Design constraints / negative prompt

Do NOT create an all-purple dashboard, dark cyberpunk/glassmorphism panels, cartoon-only analytics with unreadable tiny type, generic four-equal-card admin templates, floating random widgets without alignment, permanent confetti, bouncing charts, unrelated mascot poses, excessive shadows, or large gradients behind all the content.

Do NOT claim the original reference brands authored this file. Do NOT reproduce their logos, copyrighted illustrations, or original mascot likenesses.

## 11. Build order and acceptance checklist

1. CSS tokens, fonts, main shell / responsive navigation.
2. Greeting card and 4 metric cards; render real text and deterministic sample data.
3. Task list with working checkboxes, undo and local storage.
4. Chart + date range filters and accurate accessible labels.
5. Calendar / project details / modal or side sheet interactions.
6. Original mascot assets and motion details.
7. Keyboard flow, reduced-motion mode, mobile checks and performance polish.

Acceptance checklist:
- [ ] Data hierarchy is clear before animations load.
- [ ] At least 3 interactions are fully functional and persistent where appropriate.
- [ ] Interactive states are visible for mouse AND keyboard.
- [ ] A user can finish a task, inspect a chart value and select a calendar item.
- [ ] Reduced-motion mode keeps the app entirely usable without decorative animations.
- [ ] Desktop and mobile layouts remain readable.
- [ ] Sample data is clearly identified as example/demo data.

## 12. Ready-to-paste brief for Codex / Cursor / Claude Code

> Create an original responsive SaaS dashboard called MOMO Workspace based on the attached DESIGN.md. Use the provided color roles, type hierarchy and bento grid without copying the visual identity or mascot of referenced websites. It should look clean and professional at first glance but reveal playful pastel details and responsive motion through use. Implement a realistic dashboard including functional task checkboxes, date filters, an interactive chart, a mini content calendar, project cards, local demo persistence, loading/empty/error states and reduced-motion support. All user-facing copy should be natural Korean. Include component structure, responsive SCSS/CSS and original SVG/CSS illustrations. Prioritize legibility and motion tied to useful events, not ambient animation overload.
