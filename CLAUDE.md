# signage

Studio RYST lobby TV display (signage.ryst.in, `index.html`) and the customer quote view. Static site on GitHub Pages.

## Design and game-development skills

This repository includes seven project skills in `.claude/skills/`. Claude Code loads each skill's name and description at the start of a session and uses a skill automatically when a task matches its description. Each can also be run by name, for example `/visual-qa`.

| Skill | Use it for |
|---|---|
| `art-direction` | Look and feel before building: concept, palette roles, typography, composition, illustration and motion personality |
| `premium-ui-ux` | Building or polishing interfaces: layout, spacing scale, hierarchy, controls, states, interactions, accessibility |
| `game-ui-design` | Game screens and feedback: lobby, player identity, turns, timers, dice and moves, scoreboards, results, reconnects |
| `3d-game-graphics` | Depth and rendered scenes: choosing Canvas 2D, PixiJS or Three.js, lighting, materials, shadows, performance, WebGL fallback |
| `motion-graphics` | Anything that moves: transitions, dice rolls, token movement, card flips, celebrations, easing, reduced motion |
| `responsive-tv-design` | TV, projector and signage screens and their phone controllers: 720p/1080p/4K, safe areas, viewing distance |
| `visual-qa` | Real screenshots and checks before calling visual work done; includes `scripts/capture.mjs` and `scripts/compare.mjs` |

### How to work

- For game development or any visual redesign, use the relevant skills above before writing code, and finish every visual change with `visual-qa` screenshots at the sizes people use.
- Inspect the existing code, assets and loaded scripts before recommending or adding a library. These sites are plain HTML, CSS and JavaScript with no build step; keep it that way unless asked.
- Do not add a second rendering or animation engine where one already does the job (Canvas 2D, self-hosted Three.js r128 and GSAP already exist in the villa site).
- Do not create slash commands for these skills; they are invoked by their skill names.

### Brand context: RYST PLAY

RYST PLAY is the guest game system in the RYST-109A repository (`play.html` on phones, `display.html` on the pool TV, served by `ryst-109a-proxy`). Its identity is a premium coastal resort meets modern arcade:

| Token | Hex |
|---|---|
| Deep Teal | `#07333B` |
| Champagne Gold | `#D8B879` |
| Warm Ivory | `#F6F3EC` |
| Seafoam | `#A9CFC5` |

## graphify

This project has a knowledge graph at graphify-out/ with god nodes, community structure, and cross-file relationships.

Rules:
- When graphify-out/graph.json exists, run `graphify query "<question>"` before your first grep, search or source-file read for a codebase question, and put this rule in every subagent prompt that explores code. Read raw files only for lines the graph or an earlier read already located. Use `graphify path "<A>" "<B>"` for relationships and `graphify explain "<concept>"` for focused concepts. When the answer is under a Markdown heading, `graphify section "<heading>"` prints that section's text, so the .md need not be opened. These return a scoped subgraph, usually much smaller than GRAPH_REPORT.md or raw grep output.
- If graphify-out/wiki/index.md exists, use it for broad navigation instead of raw source browsing.
- Read graphify-out/GRAPH_REPORT.md only for broad architecture review or when query/path/explain do not surface enough context.
- After modifying code, run `graphify update .` to keep the graph current (AST-only, no API cost).
- A committed graphify-out/graph.json is rewritten whole on every build, so a large diff to it in a pull request is expected. Do not flag it as churn or suggest skipping the graph rebuild or its hooks.
