---
name: novo-endpoint
description: >-
  Adiciona um endpoint à Tarefas API seguindo as convenções do
  projeto (rota em TarefaEndpoints.cs, teste em tests/). Use
  quando pedirem um novo endpoint, rota ou recurso HTTP.
argument-hint: "[verbo] [rota] [descrição]"
allowed-tools:
  - Bash(dotnet build *)
  - Bash(dotnet test *)
---

# Novo endpoint

Pedido: $ARGUMENTS

Siga estes passos, nesta ordem:

1. Leia `src/Tarefas.Api/TarefaEndpoints.cs` e copie o estilo
   das rotas existentes (grupo `/tarefas`, `Results.*`).
2. Se precisar de armazenamento novo, altere apenas
   `TarefaRepositorio.cs`. Não coloque lógica em `Program.cs`.
3. Valide a entrada. Erro de validação devolve
   `Results.ValidationProblem` (400).
4. Escreva os testes em `tests/Tarefas.Api.Tests/`: um de
   sucesso e um de erro, usando `WebApplicationFactory<Program>`.
5. Rode `dotnet build` e `dotnet test`. Corrija até passar.
6. Responda com a lista de arquivos alterados e o resultado
   dos testes. Não faça commit.

Linhas de código com no máximo 66 colunas.
