# AGENTS.md — Guidance for AI Agents Editing This Repo

This repository is a structured Agent Skills repository for NovelSeed.

## Repo Structure

- **skills/novelseed/SKILL.md** — The main agent prompt. All methodology lives here or in references/.
- **skills/novelseed/references/** — Detailed guides loaded on-demand (not in-context by default).
- **skills/novelseed/references/genres/** — One template per genre. Add new genres here.
- **examples/** — Generic examples only. NEVER add real author works.

## SKILL.md Rules

- Keep under 500 lines. Move long content to references/.
- Write in third person. Use imperative form.
- Use ✅/❌ for do/don't lists.
- Never reference specific real novels, authors, or platforms.

## Adding a New Genre Template

1. Create `skills/novelseed/references/genres/<name>.md`
2. Template must include: world-building defaults, common tropes, reader expectations, power/relationship system structure
3. Update SKILL.md genre table

## What NOT to Commit

- Real novel content or plotlines (use generic examples only)
- Platform-specific publishing details (this is about writing, not publishing)
- Personal API keys, tokens, or credentials
- Any content from private novel works-in-progress
