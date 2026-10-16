# claude-skills

My personal [Claude Code](https://claude.com/claude-code) skills, packaged as a plugin marketplace so I can install them on any machine.

## Install

In Claude Code:

```
/plugin marketplace add helloworldiesc/freegitskills
/plugin install my-skills@claude-skills
```

To pull in new or changed skills later:

```
/plugin marketplace update claude-skills
```

If this repo is private, the machine needs git access to it (Git Credential Manager or `gh auth login`).

## Skills

| Skill | What it does |
| --- | --- |
| [`new-skill`](skills/new-skill/SKILL.md) | Adds a new skill to this repo, or edits one, and publishes it. |

## Adding a skill

Ask Claude to "save this as a skill" and the `new-skill` skill handles it. To do it by hand:

1. Create `skills/<name>/SKILL.md`:

   ```markdown
   ---
   name: <name>
   description: <What it does. Use when the user says "...", "...".>
   ---

   # <Title>

   <Instructions for Claude.>
   ```

2. Put longer reference docs in `skills/<name>/references/` and scripts in `skills/<name>/scripts/`.
3. Bump `version` in [`.claude-plugin/plugin.json`](.claude-plugin/plugin.json) so installed copies update.
4. Add a row to the table above, commit and push.

## Layout

```
.claude-plugin/
  marketplace.json   # makes the repo a marketplace with one plugin
  plugin.json        # the my-skills plugin (repo root is the plugin)
skills/
  <name>/SKILL.md    # one folder per skill
```

## Other skill collections

These aren't copied here; install them from their own repos.

- **[anthropics/skills](https://github.com/anthropics/skills)** — Anthropic's public skills, including the Word, PDF, PowerPoint and Excel document skills and skill-creator.

  ```
  /plugin marketplace add anthropics/skills
  ```

  Then run `/plugin` to browse and install its plugins.

- **[cloudflare/skills](https://github.com/cloudflare/skills)** — Cloudflare's Workers, Durable Objects, Wrangler, `cf` CLI and other platform skills (Apache-2.0).

  ```
  /plugin marketplace add cloudflare/skills
  /plugin install cloudflare@cloudflare
  ```

The skills built into the Claude desktop app (the `anthropic-skills` bundle) are licensed against copying outside Claude, so they don't belong in this repo.
