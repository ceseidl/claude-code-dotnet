English | [Português](README.pt-BR.md)

# claude-code-dotnet

Companion repository for the article "Claude Code with .NET: from
configuration to the first project". It has two parts:

- the **Claude Code configuration files** the article builds up
  step by step (`CLAUDE.md`, `.claude/settings.json` and two skills
  under `.claude/skills/`);
- the **first project** built with that setup: a small ASP.NET Core
  Minimal API (.NET 10) with an in-memory task list and integration
  tests.

## Prerequisites

- [.NET 10 SDK](https://dotnet.microsoft.com/download)
- Optional, to use the configuration:
  [Claude Code](https://code.claude.com/docs)

No database, no API keys, no network services.

## How to run

```bash
dotnet build
dotnet test
dotnet run --project src/Tarefas.Api
```

Then, in another terminal (the port is printed on startup):

```bash
curl -X POST http://localhost:5000/tarefas \
  -H "Content-Type: application/json" \
  -d '{"titulo":"Read the docs"}'
curl http://localhost:5000/tarefas
```

Expected test output: 5 passed, 0 failed.

## Endpoints

| Verb | Route | Result |
| ---- | ----- | ------ |
| GET | `/tarefas?concluida=true` | list, optional filter |
| GET | `/tarefas/{id}` | one task or 404 |
| POST | `/tarefas` | 201 + `Location`, or 400 if the title is empty |
| POST | `/tarefas/{id}/concluir` | marks as done, or 404 |

## Structure

```
CLAUDE.md                      project instructions
.claude/settings.json          shared permissions
.claude/skills/novo-endpoint/  skill: add an endpoint
.claude/skills/pronto-para-commit/  skill: pre-commit check
src/Tarefas.Api/               the Minimal API
tests/Tarefas.Api.Tests/       integration tests (xUnit)
```

## Notes

- `CLAUDE.md`, `settings.json` and `SKILL.md` follow the formats in
  the official Claude Code documentation (code.claude.com/docs).
- `.claude/settings.local.json` and `CLAUDE.local.md` are personal
  and git-ignored.
- NuGet packages come from nuget.org (see `nuget.config`).
- Domain names (routes, types) are in Portuguese on purpose, as in
  the article.
