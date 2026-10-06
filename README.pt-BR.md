[English](README.md) | Português

# claude-code-dotnet

Repositório de apoio ao artigo "Claude Code com .NET: da
Configuração ao Primeiro Projeto". Tem duas partes:

- os **arquivos de configuração do Claude Code** que o artigo
  monta passo a passo (`CLAUDE.md`, `.claude/settings.json` e duas
  skills em `.claude/skills/`);
- o **primeiro projeto** feito com essa configuração: uma Minimal
  API pequena em ASP.NET Core (.NET 10), com lista de tarefas em
  memória e testes de integração.

## Requisitos

- [.NET 10 SDK](https://dotnet.microsoft.com/download)
- Opcional, para usar a configuração:
  [Claude Code](https://code.claude.com/docs)

Sem banco de dados, sem chaves de API, sem serviços de rede.

## Como rodar

```bash
dotnet build
dotnet test
dotnet run --project src/Tarefas.Api
```

Depois, em outro terminal (a porta aparece na inicialização):

```bash
curl -X POST http://localhost:5000/tarefas \
  -H "Content-Type: application/json" \
  -d '{"titulo":"Ler a documentação"}'
curl http://localhost:5000/tarefas
```

Saída esperada dos testes: 5 aprovados, 0 com falha.

## Endpoints

| Verbo | Rota | Resultado |
| ----- | ---- | --------- |
| GET | `/tarefas?concluida=true` | lista, filtro opcional |
| GET | `/tarefas/{id}` | uma tarefa ou 404 |
| POST | `/tarefas` | 201 + `Location`, ou 400 se o título for vazio |
| POST | `/tarefas/{id}/concluir` | marca como concluída, ou 404 |

## Estrutura

```
CLAUDE.md                      instruções do projeto
.claude/settings.json          permissões compartilhadas
.claude/skills/novo-endpoint/  skill: adicionar endpoint
.claude/skills/pronto-para-commit/  skill: conferência pré-commit
src/Tarefas.Api/               a Minimal API
tests/Tarefas.Api.Tests/       testes de integração (xUnit)
```

## Notas

- `CLAUDE.md`, `settings.json` e `SKILL.md` seguem os formatos da
  documentação oficial do Claude Code (code.claude.com/docs).
- `.claude/settings.local.json` e `CLAUDE.local.md` são pessoais e
  ficam fora do git.
- Os pacotes NuGet vêm do nuget.org (veja `nuget.config`).
- Os nomes de domínio (rotas, tipos) estão em português de
  propósito, como no artigo.
