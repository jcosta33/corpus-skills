# swarm-skills

> The optional skills catalog for [Swarm](https://github.com/jcosta33/swarm) — focused agent guides in the open Agent Skills format, installable into any agent CLI.

Each skill is a self-contained folder under [`skills/`](./skills/): one `SKILL.md` with a trigger description and the working rules, plus bundled `references/` where a skill ships a fillable session frame. No scripts, no runtime — markdown an agent loads when the work matches.

The Swarm starter kit ships the three guides the core loop requires (`write-spec`, `implement-task`, `review-output`). Everything else lives here, so a workspace installs only what its work calls for.

## Install

With the [Vercel skills CLI](https://github.com/vercel-labs/skills) (works with Claude Code, Cursor, Codex, OpenCode, Gemini CLI):

```bash
# list what's available
npx skills add jcosta33/swarm-skills --list

# install one skill into the current repo
npx skills add jcosta33/swarm-skills --skill write-audit

# install globally, or for a specific agent
npx skills add jcosta33/swarm-skills --skill write-audit -g
npx skills add jcosta33/swarm-skills --skill write-audit -a claude-code
```

No CLI? Copy the folder: `cp -R skills/write-audit <your-repo>/.agents/skills/` (point your tool's skills directory at the same folder — e.g. a `.claude/skills` symlink).

## The AGENTS.md contract

Skills name abstract command slots — `cmdTest`, `cmdLint`, `cmdTypecheck` — never concrete commands. The consuming repo's `AGENTS.md` Commands table supplies the implementations. That split is what makes a skill portable: the guide carries the discipline, your repo carries the toolchain. An empty slot means **ask** — a skill never invents a command. The [Swarm starter kit](https://github.com/jcosta33/swarm) sets this contract up for you.

## Catalog

### Quality gates

| Skill | Use it when |
|---|---|
| `adversarial-review` | a deep, hostile re-review of an agent branch — re-run validation yourself, six adversarial questions, caller search |
| `spec-check` | proofreading a spec against the writing rules before work is cut from it |
| `save-findings` | closing a task — route every durable discovery to a home that outlives the session |

### Planning and decomposition

| Skill | Use it when |
|---|---|
| `split-work` | one spec needs to become several right-sized, independently verifiable tasks |
| `write-change-plan` | a structural change to an existing area needs ordered, reviewable steps |
| `write-inventory` | structural work needs a catalog of what exists before anyone plans the change |

### Document authoring

| Skill | Use it when |
|---|---|
| `write-audit` | an existing area needs an evidence-grounded picture of its risk and debt |
| `write-research` | a decision needs surveyed options and evidence before anyone commits |
| `write-rfc` | one approach should be proposed and weighed against alternatives before deciding |
| `write-prd` | new product behavior needs its outcome and audience stated before a spec exists |
| `write-bug-report` | a defect needs a reproduction and a root cause before anyone writes the fix task |
| `persona-surveyor` | breadth research — what prevails across many products, patterns, or users |

### Code authoring

| Skill | Use it when |
|---|---|
| `implement-task` | implementing a Swarm task packet, long form — supersedes the kit's core guide when you want the full session frame |
| `write-feature` | net-new behavior behind a defined surface |
| `write-fix` | a reproduced defect with a root cause |
| `write-refactor` | restructuring with behavior pinned by tests |
| `write-rewrite` | re-implementing code whose behavior changes on purpose, with the delta recorded and the rest proven preserved |
| `write-migration` | moving the code from API A to API B — green after every wave, old callsites grepped to zero |
| `write-performance` | a measured bottleneck with a target, baseline first |
| `write-testing` | adding the tests an area should already have |
| `write-documentation` | human-facing docs for a reader who hasn't read the code |
| `fix-flaky-test` | a test that fails intermittently — diagnose, don't retry-loop |

## Security

Read a skill before installing it — a skill is instructions your agent will follow. Everything here is plain markdown: no scripts, no network calls, no executables. Pin to a commit if you need a stable install.

## Relationship to the Swarm framework

These guides assume the Swarm working discipline — specs with verifiable requirements, task packets with evidence-backed claims, review packets as the durable record — but each one stands alone; install what fits your workflow. The framework, its docs, and the starter kit live at [jcosta33/swarm](https://github.com/jcosta33/swarm). This catalog is curated: skill content is edited here, and changes are planned and reviewed in the Swarm project's workspace.
