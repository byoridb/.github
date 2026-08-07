<p align="center">
  <img src="https://raw.githubusercontent.com/byoridb/.github/main/profile/byori-app-icon.png" width="140" alt="Byori">
</p>

<h1 align="center">BYORI</h1>

<p align="center"><b>Coding agents that remember why.</b></p>

<p align="center">
  Open-source tools for building software with AI agents that keep the project's
  decisions, causes, and history instead of relearning them every session.
</p>

---

## The problem we work on

```text
Session 1 — Claude Code
  ✓ found the bug   ✓ fixed it   ✓ explained why it had to be that way

A month later — new session, maybe a different agent
  "I have no memory of this project."

The same moment, with Byori
  "I remember. This bug came from decision #42, which superseded #17.
   Option B was rejected after incident #18."
```

A longer context window does not fix this. What gets lost is not text — it is the
chain that explains the code:

```text
incident ──caused_by──> bug ──fixed_by──> decision ──affects──> module
                                      └──supersedes──> previous decision
```

Vector search recalls a similar paragraph. A graph recalls the reason.

## The ecosystem

| | Project | What it is |
|---|---|---|
| 🕸 | **[Byori](https://github.com/byoridb/byori)** | A project-first native multi-agent coding workspace. Run Claude Code and Codex side by side over a shared graph memory. |
| 🗄 | **[ByoriDB](https://github.com/byoridb/byoridb)** | The graph engine beneath it — a semantic graph database in Rust with nGQL, rule inference, bitemporal history, and provenance. |
| 🖥 | **[ByoriDB Studio](https://github.com/byoridb/byoridb-studio)** | A desktop manager for browsing, querying, and administering a ByoriDB instance. |

```text
        Claude Code · Codex
                 │  MCP + skills
                 ▼
              Byori            multi-agent coding workspace
                 │  pinned HTTP/nGQL contract
                 ▼
             ByoriDB           semantic graph database
                 │
                 ▼
         ByoriDB Studio        visual management
```

Dependencies flow in one direction only. ByoriDB knows nothing about Byori; Byori installs
and manages a validated engine release.

## Quick start

```bash
curl -fsSL https://github.com/byoridb/byori/releases/latest/download/install.sh | bash
```

This installs a local single-node ByoriDB, registers the MCP server with the coding CLIs it
detects, and installs the memory skill. Everything stays on your machine — the data files and
the MCP process are local.

> [!WARNING]
> These are early projects under active development. Do not use them as the only copy of
> important data.

## License

Apache-2.0 across the ecosystem.
