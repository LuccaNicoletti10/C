# CLAUDE.md — Regras do projeto ST0C

Estas regras valem para qualquer agente que trabalhe neste repositório.

**Arquitetura operacional completa:** leia [`SYSTEM_ARCHITECTURE.md`](SYSTEM_ARCHITECTURE.md)
antes de processos formais (planejamento, revisão, ship, memória).

---

## Hierarquia do projeto

| Componente | Papel | Localização |
|------------|-------|-------------|
| **ST0C** | Produto — código, testes, docs | Este repositório |
| **gstack** | Processo e revisão | `~/.claude/skills/gstack` |
| **ruflo** | Memória semântica e coordenação | `.claude-flow/` + MCP |
| **gstack-main** | Referência no workspace — **não modificar** | `../gstack-main/` |

---

## Regras de trabalho

1. **Antes de alterar código, explique o plano** — descreva o que será feito e por quê.
2. **Antes de comandos de terminal, explique o comando** — peça confirmação para
   operações perigosas (remoção, reset, force push, etc.).
3. Construir com **arquitetura limpa, simples e escalável**.
4. **Não misturar código do gstack-main** dentro do ST0C.
5. **Nunca alterar gstack-main** a partir deste projeto.
6. **Não duplicar** o que gstack ou ruflo já resolvem — usar as ferramentas.

---

## Skill routing (gstack)

Quando o pedido do usuário corresponder a um skill gstack, invoque-o. Em dúvida, invoque.

| Intenção | Skill |
|----------|-------|
| Ideias / brainstorming de produto | `/office-hours` |
| Estratégia / escopo | `/plan-ceo-review` |
| Arquitetura | `/plan-eng-review` |
| Design / UI | `/design-consultation` ou `/plan-design-review` |
| Pipeline completo de review | `/autoplan` |
| Bug / erro | `/investigate` |
| QA / testar site | `/qa` ou `/qa-only` |
| Code review / diff | `/review` |
| Polish visual | `/design-review` |
| Ship / PR / deploy | `/ship` ou `/land-and-deploy` |
| Salvar progresso | `/context-save` |
| Retomar sessão | `/context-restore` |
| Criar issue / ticket | `/spec` |

**Navegação web:** usar `/browse` do gstack — nunca `mcp__claude-in-chrome__*`.

Lista completa de skills: `~/.claude/skills/gstack`

---

## Memória e decisões

### ruflo (memória semântica)

```bash
npx ruflo@latest memory search --query "<keywords>"
npx ruflo@latest memory store --key "<key>" --value "<data>" --namespace patterns
```

MCP configurado em `.mcp.json` (`claude-flow`). Daemon **off por padrão**.

### gstack (decisões duráveis + handoff de sessão)

- Decisões: `~/.gstack/projects/st0c/decisions.jsonl`
- Buscar: `~/.claude/skills/gstack/bin/gstack-decision-search --recent 5`
- Registrar: `~/.claude/skills/gstack/bin/gstack-decision-log '{"decision":"...","rationale":"...","scope":"repo","source":"agent","confidence":8}'`
- Handoff: `/context-save` e `/context-restore`

**gbrain:** desligado por padrão. Ativar só se wiki semântica separada for necessária.

---

## Integração ruflo (Claude Code)

- Config: `.claude-flow/config.yaml`
- Hooks: `.claude/settings.json` (autoExecute habilitado)
- Skills ruflo locais: `.claude/skills/` (8 skills de coordenação)
- Memória: `.claude-flow/data/` + `.claude/memory.db`

Comandos úteis:

```bash
npx ruflo@latest doctor --fix
npx ruflo@latest hooks pre-task --description "tarefa"
```

Swarm e daemon são **opcionais** — ver `SYSTEM_ARCHITECTURE.md` §12.

---

## Documentação do produto

| Tipo | Onde |
|------|------|
| Visão | `README.md`, `docs/product/` |
| Arquitetura | `docs/architecture/` |
| ADRs | `docs/adr/` |
| Processo operacional | `SYSTEM_ARCHITECTURE.md` |
