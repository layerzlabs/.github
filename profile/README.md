# layerzlabs

Open integration surfaces for [Layerz](https://layerz.cc) — structured financial modeling infrastructure.

The repos here are not the product. They are **entry points**: open standards, tools, plugins, and recipes that let AI agents and finance practitioners work with structured financial models — without going through the web interface.

---

## Repos

### [finance-cookbook](https://github.com/layerzlabs/finance-cookbook)

Curated recipes for doing financial work with AI agents: prompts and patterns for FP&A, modeling and reporting, battle-tested in the field. The lowest-friction entry point: copy a prompt, use it now.

**We share the recipe, not the black box.** The cookbook ships prompts you can read, audit and own, never installable skills. Two kinds: *working prompts* that do the task in-session, and *builder prompts* that have Claude forge or harden your own skill, script or `FINANCE.md`.

Each recipe names where a prompt stops being enough, and points back to `finance-md` (structure) and `layerz-mcp` (persistence) when it does.

→ [Recipes · Template · Contributing](https://github.com/layerzlabs/finance-cookbook)

---

### [finance-md](https://github.com/layerzlabs/finance-md)

The standard for encoding financial conventions as machine-readable files.

A `FINANCE.md` file placed in a financial modeling project encodes the conventions that apply to all models in that project: EBITDA definition, FX policy, fiscal year, normalization rules. Any agent that reads it knows the rules — without being told again at every session.

```yaml
---
finance_md: "0.1"
model_name: "Project Granite — LBO model"
currency: EUR
glossary:
  Marge brute commerciale: "Revenue minus purchase cost only. Excludes logistics."
---

## EBITDA

Excludes IFRS16 — PE sponsor convention. Operating leases stay above EBITDA
as rent expense.

## Currency & FX

Single reporting currency (EUR). Foreign subsidiaries translated at closing
rate for BS, average for P&L.
```

→ [Spec · Examples · Template](https://github.com/layerzlabs/finance-md)

---

### [layerz-mcp](https://github.com/layerzlabs/layerz-mcp)

The Layerz MCP plugin for creating and editing financial models from the terminal — distributed across the major MCP clients (Claude Code, OpenAI Codex CLI, Claude Desktop, MCP Inspector).

One install per client. Once registered, your agent gets financial modeling expertise and the full Layerz API surface — so it can build a P&L model autonomously via the MCP tool calls.

```bash
# Claude Code
claude plugin marketplace add layerzlabs/layerz-mcp
# then in Claude Code: /plugin install layerz

# OpenAI Codex CLI
codex mcp add layerz --url https://app.layerz.cc/mcp && codex mcp login layerz
```

---

## What is Layerz

Layerz separates the **structure** of a financial model (logic, DAG of variables, timelines) from its **data** (values, scenarios). The structure is versioned, reusable, and readable by AI agents. Excel remains a compatibility output — not the source of truth.

[layerz.cc](https://layerz.cc) · [API reference](https://app.layerz.cc/for-agents)
