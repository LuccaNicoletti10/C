# CLAUDE.md — Regras do projeto ST0C

Estas regras valem para qualquer agente que trabalhe neste repositório.

## Hierarquia do projeto

- **ST0C é o projeto principal.** Todo o desenvolvimento real acontece aqui.
- **gstack-main é apenas uma ferramenta / skill pack auxiliar.** Não é o projeto
  principal e não deve ser tratado como tal.
- **ruflo é um agente / MCP auxiliar**, usado por trás para apoiar o trabalho.

## Regras de trabalho

1. **Antes de alterar qualquer código, explique o plano** — descreva o que será feito
   e por quê antes de editar arquivos.
2. **Antes de executar comandos de terminal, explique o comando** e, no caso de
   comandos perigosos (remoção, sobrescrita, reset, etc.), peça confirmação.
3. O projeto deve ser construído com **arquitetura limpa, simples e escalável**.
4. **Não misture código do gstack-main dentro do ST0C sem necessidade.** Use gstack
   apenas como referência/ferramenta.
5. **Nunca altere nada dentro de gstack-main** a partir deste projeto.
6. Mantenha a organização profissional do repositório.

## Resumo

| Componente   | Papel                          |
| ------------ | ------------------------------ |
| ST0C         | Projeto principal              |
| gstack-main  | Ferramenta / skill pack        |
| ruflo        | Agente / MCP auxiliar          |
