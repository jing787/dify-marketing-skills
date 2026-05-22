# Dify Marketing Skills

Claude Code skills for multilingual marketing content generation, optimized for [Dify](https://dify.ai) and its Japan operating entity, [LangGenius K.K. (株式会社LangGenius)](https://langgenius.co.jp/).

These skills give Claude Code (or any compatible AI agent supporting the [Agent Skills](https://www.anthropic.com/news/agent-skills) spec) the context, conventions, and brand rules required to produce on-brand B2B marketing copy across three languages: Traditional Chinese, Japanese, and English.

## Skills

| Skill | Purpose | Output |
|-------|---------|--------|
| [`dify-social-content`](skills/dify-social-content/SKILL.md) | LinkedIn + X (Twitter) social posts | Conversational, multilingual posts with proper LangGenius K.K. brand exposure |
| [`dify-press-release`](skills/dify-press-release/SKILL.md) | Full press releases (PR Times-ready) | Four scenarios: product release, event pre-announcement, event recap, partnership/customer announcement |

## What's in each Skill

Each `SKILL.md` is a self-contained instruction document containing:

- **YAML frontmatter** — trigger conditions, version, metadata
- **Persona setting** — defines Claude's role and voice
- **Before-starting context check** — what to verify before writing
- **Mode definitions** — different output patterns for different scenarios
- **Brand naming rules** — strict conventions for "株式会社LangGenius / LangGenius K.K." exposure
- **Localization style guides** — for Traditional Chinese, Japanese, English
- **Pre-publication checklist** — self-verification before delivering output
- **Proactive triggers** — when Claude should flag issues to the user
- **Data integration** — references to verified public data sources

## Install (Claude Code)

Clone this repo into your Claude Code skills directory:

```bash
git clone https://github.com/jing787/dify-marketing-skills.git ~/.claude/skills/dify-marketing-skills
```

Or copy individual skills:

```bash
cp -r skills/dify-social-content ~/.claude/skills/
cp -r skills/dify-press-release ~/.claude/skills/
```

Restart Claude Code, and the skills will be auto-discovered.

## Usage

Once installed, Claude will automatically pick up the right skill when you mention relevant keywords. Examples:

```
"Write a social post for this AWS Summit article: [URL]"
→ Triggers dify-social-content

"日本の AWS Summit 出展についての PR 稿を書いてください"
→ Triggers dify-press-release (Mode 2: event pre-announcement)

"PR for our new partnership with [Partner Co.]"
→ Triggers dify-press-release (Mode 4: partnership announcement)
```

## Internal References (Forking)

These skills reference two internal Notion databases used by the LangGenius K.K. marketing team:

- **Dify Public Data Vault** — verified public metrics, customer names, milestone dates
- **Dify Japanese Terminology Glossary** — confirmed Japanese product/feature naming (katakana vs English vs kanji)

If you fork this repo for your own organization, replace `[INTERNAL_NOTION_URL]` placeholders with your own data sources, or remove those references and adapt the skills to your context.

## File Naming Convention

- **Generic (multilingual)**: `dify-{purpose}-SKILL.md` — outputs in 繁中 / 日本語 / English
- **Japan-specific**: `dify-{purpose}-Japan-SKILL.md` — outputs in Japanese only

## Companion Skills (not in this repo)

These skills are referenced but not included here (internal-only):

- `dify-data-vault` — interface to the internal Public Data Vault
- `dify-term-check` — Japanese terminology lookup
- `dify-article-review` — review of agency-written Japanese articles
- `dify-brand` — Dify visual/brand execution rules

## License

MIT — see [LICENSE](LICENSE).

## Author

Jing Yan ([@jing787](https://github.com/jing787)) — LangGenius K.K. (株式会社LangGenius) Marketing

## Disclaimer

These skills are designed for Dify / LangGenius K.K. marketing operations. While they're shared publicly as a reference for how to structure B2B marketing skills for AI agents, the boilerplates and example metrics in them reflect LangGenius K.K.'s own brand and verified data. If you fork these skills, adapt the brand naming rules, boilerplates, and reference data to your own organization.
