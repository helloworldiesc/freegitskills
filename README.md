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

### Mine

| Skill | What it does |
| --- | --- |
| [`new-skill`](skills/new-skill/SKILL.md) | Adds a new skill to this repo, or edits one, and publishes it. |

### From Anthropic

Copied from [anthropics/skills](https://github.com/anthropics/skills) at [`dbd4588`](https://github.com/anthropics/skills/tree/dbd4588f9e1033efb41dad4bef2f7947c8993d44/skills/skill-creator). Apache-2.0; the license is in the skill's folder.

| Skill | What it does |
| --- | --- |
| [`skill-creator`](skills/skill-creator/SKILL.md) | Drafts new skills, tests them with evals, and tunes their descriptions. |

### From Cloudflare

Copied from [cloudflare/skills](https://github.com/cloudflare/skills) v1.0.2 at [`5339598`](https://github.com/cloudflare/skills/tree/53395984c3ea1925d00fce03b266112302f050e6/skills). Apache-2.0; see [`licenses/cloudflare-skills-LICENSE`](licenses/cloudflare-skills-LICENSE). Only the skills are copied, not Cloudflare's MCP server.

| Skill | What it does |
| --- | --- |
| [`cloudflare`](skills/cloudflare/SKILL.md) | Picks the right Cloudflare products for a project. |
| [`agents-sdk`](skills/agents-sdk/SKILL.md) | Builds and debugs apps on the Cloudflare Agents SDK. |
| [`basin`](skills/basin/SKILL.md) | Basin analytics: pipelines, catalog and SQL over R2 Iceberg tables. |
| [`cf-cli`](skills/cf-cli/SKILL.md) | Cloudflare's `cf` CLI: sign-in, deploys, DNS, D1, KV, R2. |
| [`cloudflare-email-service`](skills/cloudflare-email-service/SKILL.md) | Email Sending and Email Routing setup. |
| [`cloudflare-one`](skills/cloudflare-one/SKILL.md) | Zero Trust / SASE design and troubleshooting. |
| [`cloudflare-one-migrations`](skills/cloudflare-one-migrations/SKILL.md) | Planning a move from another VPN or SASE vendor. |
| [`durable-objects`](skills/durable-objects/SKILL.md) | Durable Objects for state and coordination. |
| [`k2`](skills/k2/SKILL.md) | K2 / K2 Streams durable logs. |
| [`nextjs-on-cloudflare`](skills/nextjs-on-cloudflare/SKILL.md) | Next.js on Workers with vinext. |
| [`sandbox-stable`](skills/sandbox-stable/SKILL.md) | Sandbox apps on stable `@cloudflare/sandbox`. |
| [`sandbox-next`](skills/sandbox-next/SKILL.md) | Sandbox apps on the `@next` preview SDK. |
| [`sandbox-migrate-to-next`](skills/sandbox-migrate-to-next/SKILL.md) | Moving a Sandbox app from stable to `@next`. |
| [`turnstile-spin`](skills/turnstile-spin/SKILL.md) | Adding or fixing Turnstile bot checks. |
| [`web-perf`](skills/web-perf/SKILL.md) | Core Web Vitals and Lighthouse performance work. |
| [`workers-best-practices`](skills/workers-best-practices/SKILL.md) | Production Workers code and config review. |
| [`workers-profiling`](skills/workers-profiling/SKILL.md) | CPU and memory profiling of deployed Workers. |
| [`wrangler`](skills/wrangler/SKILL.md) | Wrangler commands in projects with a Wrangler config. |

If the `cloudflare` plugin or the app's built-in skill-creator is also installed, Claude will see two copies of those skills. Keep one or the other.

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
licenses/            # licenses for skills copied from other repos
```

## Upstream sources

The copied skills won't update on their own. To get newer versions, copy them again from upstream, or install the upstream plugins directly instead:

- **[anthropics/skills](https://github.com/anthropics/skills)** — Anthropic's public skills, including the Word, PDF, PowerPoint and Excel document skills. Run `/plugin marketplace add anthropics/skills`, then `/plugin` to browse.
- **[cloudflare/skills](https://github.com/cloudflare/skills)** — `/plugin marketplace add cloudflare/skills`, then `/plugin install cloudflare@cloudflare`. That also includes Cloudflare's MCP server.

## Not included

deep-research, google-workspace, import-memory and morning come built into the Claude desktop app. They aren't published anywhere public, and their license doesn't allow copying them outside Claude, so they stay in the app.
