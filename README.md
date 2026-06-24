# ST0C

ST0C é o **projeto principal** deste workspace — produto, código e documentação
versionada vivem aqui.

## Documentação

| Documento | Conteúdo |
|-----------|----------|
| [**SYSTEM_ARCHITECTURE.md**](SYSTEM_ARCHITECTURE.md) | Arquitetura operacional — ferramentas, fluxos, source of truth |
| [**CLAUDE.md**](CLAUDE.md) | Regras para agentes + skill routing |
| [**docs/**](docs/) | Documentação do produto (visão, arquitetura, ADRs) |

## Stack operacional

```
ST0C (produto)
  ├── Cursor        → IDE + agent (edição diária)
  ├── Claude Code   → agente principal (terminal, gstack, ship)
  ├── gstack        → processo e revisão (plan → review → QA → ship)
  └── ruflo         → memória semântica e coordenação
```

## Estrutura do repositório

```
ST0C/
├── SYSTEM_ARCHITECTURE.md   # Como as ferramentas se coordenam
├── CLAUDE.md                # Regras + skill routing
├── README.md                # Este arquivo
├── docs/
│   ├── product/             # Visão, requisitos, roadmap
│   ├── architecture/        # Diagramas e visão técnica
│   └── adr/                 # Architecture Decision Records
├── .cursor/rules/           # Regras permanentes no Cursor
├── .claude-flow/            # Runtime ruflo (config versionada; data/ ignorada)
└── src/                     # Código-fonte (quando existir)
```

## Workspace externo (não modificar)

```
C/
├── ST0C/         ← você está aqui
├── gstack-main/  ← referência gstack (não é o produto)
└── c.com/        ← outros projetos
```

## Quick start

### 1. Validar setup

```bash
cd ST0C
npx ruflo@latest doctor --fix
```

### 2. Iniciar sessão de trabalho

```bash
npx ruflo@latest memory search --query "<tema>"
# No Claude Code: /context-restore
```

### 3. Feature nova

```
/office-hours → /autoplan → /spec → implementar → /review → /ship
```

Detalhes completos em [SYSTEM_ARCHITECTURE.md](SYSTEM_ARCHITECTURE.md).

## Princípios

1. ST0C é sempre o produto; gstack e ruflo são ferramentas de apoio.
2. Plano antes de código.
3. Arquitetura limpa, simples e escalável.
4. Não duplicar o que as ferramentas já resolvem.
