# Tarefas API

API mínima em ASP.NET Core (.NET 10) com lista de tarefas em
memória. Visão geral e como rodar: @README.md

## Comandos

- Build: `dotnet build`
- Testes: `dotnet test`
- Rodar a API: `dotnet run --project src/Tarefas.Api`
- Pacotes NuGet: sempre com
  `--source https://api.nuget.org/v3/index.json`

## Estrutura

- `src/Tarefas.Api/Program.cs`: só composição (DI e rotas)
- `src/Tarefas.Api/TarefaEndpoints.cs`: todas as rotas
- `src/Tarefas.Api/TarefaRepositorio.cs`: armazenamento
- `tests/Tarefas.Api.Tests/`: testes de integração (xUnit)

## Convenções

- C# 14, `Nullable` habilitado, namespaces com escopo de arquivo.
- Linhas de código com no máximo 66 colunas.
- Rotas em `/tarefas`, nomes de domínio em português.
- Sem regra de negócio em `Program.cs`.
- Erros de validação voltam como `ValidationProblem` (400).
- Todo endpoint novo vem com pelo menos um teste de sucesso
  e um de erro.

## Fluxo de trabalho

- Antes de mudar mais de um arquivo, proponha um plano curto.
- Rode `dotnet build` e `dotnet test` antes de dizer que
  terminou.
- Não faça commit nem push sem eu pedir.
- Nunca leia nem escreva arquivos `.env`.
