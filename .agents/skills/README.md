# Skills

Nine task modules, auto-activated by the agent from the `description:` line when the request matches.
Nothing here is injected into every turn — the description is the trigger, the body loads on demand.

| Skill | Use it for |
|-------|-----------|
| [`business`](business/SKILL.md) | Scoping, pricing, unit economics, go/no-go, positioning |
| [`coding`](coding/SKILL.md) | Implementation, debugging, refactoring, tests, review |
| [`content`](content/SKILL.md) | Prose, docs, READMEs, commit messages, copy |
| [`vps`](vps/SKILL.md) | Servers, SSH, TLS, deploys, firewalls, incidents |
| [`automation`](automation/SKILL.md) | Scripts, cron, timers, scheduled work, workflows |
| [`api`](api/SKILL.md) | Endpoints, REST, auth, webhooks, rate limits, clients |
| [`data`](data/SKILL.md) | SQL, migrations, indexes, integrity, slow queries |
| [`files`](files/SKILL.md) | Moving, renaming, searching, cleaning, bulk edits |
| [`web`](web/SKILL.md) | HTML, CSS, frontend, a11y, performance, scraping |

Conflict rules: a skill is craft on top of `SOUL.md` and `AGENTS.md`, never a replacement. When a skill
contradicts an explicit user instruction, the user wins. When two skills match one task, load the more
specific one and say which.

Adding a skill: new directory, `SKILL.md` with `name` and `description` frontmatter, rules as concrete
imperatives with a "Done when" line. Keep the description trigger-rich — it is the only part read
every time.
