# How to Set Up Agent Teams

## English

### Prerequisites

- **Claude Code v2.1.32+** — check with `claude --version`
- Agent Teams are experimental and disabled by default

### Setup

**1. Create a branch:**
```bash
git checkout -b agent-teams
```

**2. Copy the blueprint setup into your project:**
```bash
cp -r .claudeAgentTeams/agents/ .claude/agents/
cp -r .claudeAgentTeams/skills/ .claude/skills/
cp -r .claudeAgentTeams/templates/ .claude/templates/
cp -r .claudeAgentTeams/workflows/ .claude/workflows/
cp .claudeAgentTeams/CLAUDE.md .claude/CLAUDE.md
```

**3. Enable the feature in `.claude/settings.json`:**
```json
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

### What You Get

The setup includes the following agents: **Lead** (coordinates), **Architect** (plans), **Developer** (implements), **Test Engineer** (test design), **Security Engineer** (security), **Reviewer** (quality & commit).

Two skills: `/project-init` (generates `CLAUDE.md` with project context) and `/ensure-plans-dir` (prepares the plan directory).

---

## Deutsch

### Voraussetzungen

- **Claude Code v2.1.32+** — prüfen mit `claude --version`
- Agent Teams sind experimentell und standardmäßig deaktiviert

### Setup

**1. Branch anlegen:**
```bash
git checkout -b agent-teams
```

**2. Blueprint-Setup ins Projekt kopieren:**
```bash
cp -r .claudeAgentTeams/agents/ .claude/agents/
cp -r .claudeAgentTeams/skills/ .claude/skills/
cp -r .claudeAgentTeams/templates/ .claude/templates/
cp -r .claudeAgentTeams/workflows/ .claude/workflows/
cp .claudeAgentTeams/CLAUDE.md .claude/CLAUDE.md
```

**3. Feature in `.claude/settings.json` aktivieren:**
```json
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

### Was enthalten ist

Das Setup bringt folgende Agents mit: **Lead** (koordiniert), **Architect** (plant), **Developer** (implementiert), **Test Engineer** (Testdesign), **Security Engineer** (Sicherheit), **Reviewer** (Qualität & Commit).

Dazu zwei Skills: `/project-init` (generiert `CLAUDE.md` mit Projektkontext) und `/ensure-plans-dir` (bereitet den Plan-Ordner vor).
