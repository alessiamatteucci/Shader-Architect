# Shader Architect

**Una skill per progettare, creare e rifinire shader nativi in Figma tramite Figma MCP, con Claude Code o Codex.**

Descrivi un materiale o allega una reference — vetro iridescente, cromo liquido, superfici olografiche, distorsioni organiche, noise animato — e l'assistente lo traduce in uno shader Figma controllabile: brief tecnico, parametri, codice WebGPU/WGSL, creazione tramite MCP e link per provarlo in Figma.

*English summary below.*

---

## Cosa fa

Shader Architect lavora in tre modalità, che puoi richiamare con un'etichetta o semplicemente descrivendo cosa vuoi:

| Modalità | Cosa ottieni |
| --- | --- |
| `/ANALYZE` | Analisi di una reference (forma, materiale, luce, trasparenza) e proposta tecnica, senza toccare Figma |
| `/CREATE` | Progettazione e creazione di un nuovo shader nel tuo account Figma |
| `/REFINE` | Modifica mirata di uno shader esistente, preservando ciò che già funziona |

La skill si occupa delle **decisioni creative**: scelta tra `fill` ed `effect`, costruzione procedurale (SDF, Voronoi, noise, domain warp), ottica dei materiali, design dei controlli, verifica visiva. Il **contratto di esecuzione** resta quello della skill ufficiale `figma-shaders` e del server MCP di Figma, che l'assistente rilegge ogni volta prima di scrivere codice.

## Requisiti

- **Claude Code** o **Codex** (o un altro agente che supporti skill locali e MCP)
- **Server MCP ufficiale di Figma** collegato, con gli strumenti `create_shader`, `get_shader`, `update_shader`, `list_shaders`
- **Plugin/skill Figma** installato, con `figma-shaders`

Senza il collegamento a Figma la skill produce comunque un brief tecnico, etichettato chiaramente come *brief only — not created in Figma*.

## Installazione

Clona la repo:

```bash
git clone https://github.com/alessiamatteucci/Shader-Architect.git
```

**Claude Code** — copia la cartella della skill tra le skill personali:

```bash
mkdir -p ~/.claude/skills && cp -R Shader-Architect/shader-architect ~/.claude/skills/
```

**Codex** — copia la cartella tra le skill di Codex:

```bash
mkdir -p ~/.codex/skills && cp -R Shader-Architect/shader-architect ~/.codex/skills/
```

In alternativa, apri l'assistente nella cartella della repo e scrivi: *«Leggi `shader-architect/SKILL.md` e usa Shader Architect per la richiesta seguente.»*

## Esempio

```text
/CREATE
Crea uno shader Figma con gocce di vetro organiche e sparse.
Devono distorcere delicatamente l'immagine ricevuta in ingresso,
con riflessi rosa e ciano discreti sui bordi.
Voglio controllare dimensione, distribuzione, distorsione e iridescenza.
Per ora statico. Trasparente fuori dalle gocce.
```

Alla fine ricevi nome, tipo, ID dello shader, i controlli disponibili, lo stato di verifica e un link per provarlo in Figma.

Per una guida passo passo con altre richieste pronte da copiare, leggi **[GUIDA_COSTRUISCI_IL_TUO_SHADER.md](GUIDA_COSTRUISCI_IL_TUO_SHADER.md)**.

## Struttura

```
shader-architect/
├── SKILL.md                         # istruzioni principali e scelta della modalità
├── references/
│   ├── workflows.md                 # flussi CREATE / REFINE / ANALYZE
│   ├── figma-mcp-workflow.md        # adattatore per Figma MCP e invarianti di runtime
│   ├── fundamentals-and-patterns.md # coordinate, maschere, pattern procedurali, loop
│   ├── materials-and-optics.md      # vetro, cromo, iridescenza, olografia, liquidi
│   ├── parameter-design.md          # progettazione dei controlli
│   ├── quality-and-debugging.md     # verifica e diagnosi
│   └── prompt-template.md           # template del brief tecnico
└── examples/                        # cinque ricette di partenza
    ├── iridescent-glass.md
    ├── liquid-chrome.md
    ├── holographic-material.md
    ├── organic-distortion.md
    └── animated-noise.md
```

## Note

- Gli esempi sono **ricette di progetto**, non shader già compilati o verificati visivamente.
- «Compilato» e «verificato visivamente» sono stati distinti: la skill dichiara sempre quale dei due è stato raggiunto.
- Il contratto tecnico è stato verificato il 20 ottobre 2026 sulla skill ufficiale `figma-shaders` del plugin Figma per Claude Code. Le API di Figma possono cambiare: la skill rilegge sempre la documentazione ufficiale installata prima di eseguire.
- La repo non contiene credenziali, immagini di reference o plugin da installare dentro Figma.

---

## English summary

**Shader Architect** is an agent skill for designing, creating and refining native Figma shaders through the official Figma MCP server, from Claude Code or Codex. Describe a material or attach a reference and the assistant turns it into a controllable Figma shader — implementation brief, parameter set, WebGPU/WGSL source, creation via MCP and a try-in-Figma link.

- **Modes:** `/ANALYZE` (study a reference, no changes), `/CREATE` (new shader), `/REFINE` (targeted edit preserving what works).
- **Requires:** the official Figma MCP server and the `figma-shaders` skill. Without them, the skill outputs a clearly labelled technical brief.
- **Install:** copy the `shader-architect/` folder into `~/.claude/skills/` (Claude Code) or `~/.codex/skills/` (Codex).
- The skill answers in the user's language (Italian or English); briefs and code identifiers are written in English.

## Licenza

[MIT](LICENSE) © 2026 Alessia Matteucci
