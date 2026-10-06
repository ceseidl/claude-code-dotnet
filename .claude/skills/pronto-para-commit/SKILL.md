---
name: pronto-para-commit
description: >-
  Confere se as mudanças atuais estão prontas para commit e
  sugere a mensagem.
disable-model-invocation: true
allowed-tools:
  - Bash(dotnet build *)
  - Bash(dotnet test *)
  - Bash(git diff *)
  - Bash(git status *)
---

# Pronto para commit?

## Arquivos alterados

!`git status --short`

## Instruções

1. Rode `dotnet build` e `dotnet test`.
2. Olhe `git diff` e aponte: linhas com mais de 66 colunas,
   endpoint sem teste, segredo ou `.env` no diff.
3. Se tudo estiver certo, sugira uma mensagem de commit em uma
   linha (imperativo, até 72 caracteres).
4. Não execute `git commit`. Quem decide é o desenvolvedor.
