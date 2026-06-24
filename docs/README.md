# Documentação ST0C

Documentação versionada do produto. Processo operacional (como usar ferramentas) fica em
[`../SYSTEM_ARCHITECTURE.md`](../SYSTEM_ARCHITECTURE.md) — não duplicar aqui.

## Estrutura

| Pasta | Conteúdo | Source of truth para |
|-------|----------|----------------------|
| [`product/`](product/) | Visão, requisitos, roadmap | O que estamos construindo |
| [`architecture/`](architecture/) | Diagramas, visão técnica | Como o sistema funciona |
| [`adr/`](adr/) | Architecture Decision Records | Decisões arquiteturais maiores |

## Quando escrever onde

- **Decisão operacional do dia** → gstack `decisions.jsonl` (não commit)
- **Decisão arquitetural significativa** → ADR em `adr/` (commit no repo)
- **Plano de feature** → GitHub Issue (via gstack `/spec`)
- **Release notes** → CHANGELOG (via gstack `/document-release`)
