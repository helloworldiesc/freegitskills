---
name: new-skill
description: Add a new skill to the user's personal claude-skills repo, or change one already in it. Use when the user says "add this as a skill", "save this as a skill", "make a skill for X", "put this in my skills repo", or asks to edit or remove one of their own skills. Not for Anthropic's built-in skills or other plugins.
---

# Add a skill to the personal skills repo

This repo is a Claude Code plugin marketplace with one plugin, `my-skills`, at the repo root. Every folder under `skills/` is one skill.

## Where the repo is

The local clone is normally at `C:\Users\gates\claude-skills`. If it isn't there, ask the user where it is, or clone `https://github.com/helloworldiesc/freegitskills`. Edit the clone, never the installed copy under `~/.claude/plugins/` — that one is overwritten on update.

## Steps

1. Pick a short kebab-case name (`weekly-report`, `deploy-site`). Check `skills/` so you don't clash with an existing one.
2. Create `skills/<name>/SKILL.md`:

   ```markdown
   ---
   name: <name>
   description: <What it does, then "Use when ..." with the phrases the user would actually say.>
   ---

   # <Title>

   <Instructions Claude should follow, written as steps or rules.>
   ```

   The `description` is the only part Claude sees before the skill loads, so it decides whether the skill ever triggers. Name concrete trigger phrases and say what it is *not* for if there's a nearby skill it could be confused with.
3. Keep `SKILL.md` focused. Put long reference material in `skills/<name>/references/*.md` and scripts in `skills/<name>/scripts/`, and tell the reader in `SKILL.md` when to open each one.
4. Bump the patch number of `version` in `.claude-plugin/plugin.json` (`0.1.0` → `0.1.1`). Without a bump, machines that already installed the plugin may keep the cached copy.
5. Add a row for the skill to the table in `README.md`.
6. Commit and push with the user's go-ahead:

   ```bash
   git add -A
   git commit -m "Add <name> skill"
   git push
   ```

7. Tell the user to run `/plugin marketplace update claude-skills` (or restart Claude Code) to pick up the change.

If the `skill-creator` skill is available, use it to draft and test the skill's content; this skill only covers where it goes and how it's published.

## Never copy in

Don't add Anthropic's built-in skills (docx, pdf, pptx, xlsx and the rest in the app's `anthropic-skills` bundle) or another plugin's skills unless their license allows it. The built-in ones are licensed against copying outside Claude.
