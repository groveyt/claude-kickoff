# claude-kickoff

A Claude Code slash command that turns "I have a new project idea" into a clean, structured git repo.

It solves two recurring problems:

- New projects start without a clear goal, audience, constraints, or deliverable.
- New projects end up scattered across `~/Downloads/`, `~/Desktop/`, or a half-initialized folder with no git history.

`/kickoff` runs a 4-question interview, then scaffolds `~/projects/<name>/` with a `CLAUDE.md`, `.gitignore`, `git init`, and (optionally) a GitHub remote via `gh`.

## Install

### Option 1: single-file install

```bash
mkdir -p ~/.claude/commands
curl -fsSL https://raw.githubusercontent.com/OWNER/claude-kickoff/main/commands/kickoff.md \
  -o ~/.claude/commands/kickoff.md
```

### Option 2: git clone

```bash
git clone https://github.com/OWNER/claude-kickoff.git
mkdir -p ~/.claude/commands
cp claude-kickoff/commands/kickoff.md ~/.claude/commands/kickoff.md
```

## Usage

In any Claude Code session:

```
/kickoff
```

The command will ask 4 questions, propose a kebab-case name, then scaffold the project.

## Requirements

- [Claude Code](https://claude.com/claude-code) — required
- [`gh` CLI](https://cli.github.com/) — optional, only used if you want a GitHub remote created automatically

## Configuration

At the top of `kickoff.md` there's a Configuration block. You can override defaults before running:

- `PROJECTS_ROOT` — default `~/projects/`
- `CREATE_GITHUB_REMOTE` — `auto` (default) / `yes` / `no`
- `GITHUB_VISIBILITY` — `--private` (default) / `--public`

## Sample interaction

```
You: /kickoff
Claude: What is the goal of this project? (one sentence)
You: A small CLI that backs up my Notion pages to markdown.
Claude: Who is the audience or user of this project?
You: Just me, running it locally.
... (2 more questions, then a name suggestion) ...
Claude: Project `notion-backup` created at ~/projects/notion-backup/
        Remote: https://github.com/you/notion-backup
```

## License

MIT — see [LICENSE](LICENSE).
