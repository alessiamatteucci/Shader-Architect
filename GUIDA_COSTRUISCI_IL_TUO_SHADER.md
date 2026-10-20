# Costruisci il tuo shader con Shader Architect

Shader Architect trasforma un'idea o una reference in uno shader nativo Figma, tramite un assistente collegato agli strumenti Figma MCP. Puoi descrivere il risultato in italiano: la skill prepara il brief tecnico in inglese e gestisce il codice.

## 1. Metti a disposizione la skill

Clona la repo (o scarica lo ZIP) e conserva la cartella `shader-architect` completa: `SKILL.md`, `references` ed `examples` lavorano insieme. Le reference incluse sono documenti tecnici; le tue immagini di riferimento vanno allegate quando servono.

In un ambiente che supporta skill locali, rendi disponibile questa cartella tramite il suo sistema di skill. Per Claude Code la cartella va in `~/.claude/skills/shader-architect`; per Codex in `~/.codex/skills/shader-architect` (vedi il README per i comandi).

Puoi iniziare anche senza installarla, aprendo l'assistente nella cartella della repo e scrivendo:

> Leggi `shader-architect/SKILL.md` e usa Shader Architect per la richiesta seguente.

In altri ambienti, compresi Claude o ChatGPT, verifica che l'assistente possa leggere anche i file di supporto. Se l'ambiente non carica skill, fornisci `SKILL.md` come istruzioni e i documenti necessari come contesto. Il solo caricamento dello ZIP non garantisce attivazione, persistenza o accesso agli strumenti.

## 2. Verifica il collegamento a Figma

Per creare davvero uno shader servono gli strumenti Figma MCP per creazione, lettura e aggiornamento, oltre alle istruzioni ufficiali `figma-shaders`. La skill li verifica prima dell'esecuzione. Se mancano, può preparare un brief tecnico, ma deve dirti che lo shader non è stato creato.

## 3. Scegli la modalità

| Scrivi | Per ottenere |
| --- | --- |
| `/ANALYZE` | Analisi di una reference e proposta tecnica, senza modificare Figma |
| `/CREATE` | Progettazione e creazione di un nuovo shader |
| `/REFINE` | Modifica mirata di uno shader esistente |

Sono etichette comprese dall'assistente, non pulsanti o comandi installati in Figma. Puoi anche scrivere normalmente: «crea uno shader…».

## 4. Descrivi ciò che vuoi vedere

Indica materiale, forme, colori, trasparenza, movimento e controlli. Allega un'immagine se vuoi seguire una reference. Per una modifica, indica anche l'ID dello shader e cosa deve restare invariato.

Esempio pronto da copiare dopo aver caricato la skill:

```text
/CREATE
Crea uno shader Figma con gocce di vetro organiche e sparse.
Devono distorcere delicatamente l'immagine ricevuta in ingresso,
con riflessi rosa e ciano discreti sui bordi.
Voglio controllare dimensione, distribuzione, distorsione e iridescenza.
La composizione deve restare stabile quando cambio i riflessi.
Per ora statico. Trasparente fuori dalle gocce.
```

Per partire dall'immagine senza creare ancora:

```text
/ANALYZE
Analizza la reference allegata: forma, materiale, luce e trasparenza.
Dimmi quali elementi puoi ricreare con uno shader e quali richiedono
contenuti o livelli aggiuntivi. Distingui ciò che osservi da ciò che deduci.
```

## 5. Lascia che la skill costruisca lo shader

L'assistente sceglie il tipo adatto: **fill** per generare pattern e superfici; **effect** per trasformare un raster in ingresso. Un fill con aspetto vetroso non può automaticamente rifrangere ciò che sta dietro. Anche per un effect occorre verificare che il contenuto desiderato sia effettivamente nell'input.

Il flusso operativo è: breve progetto visivo → controlli → creazione della struttura iniziale → lettura del sorgente → codice completo → aggiornamento. Se il tuo account propone più piani, può servire scegliere quello proprietario dello shader.

## 6. Apri e valuta il risultato

Alla fine ricevi nome, tipo, ID e un link per provarlo in Figma. Controlla l'aspetto alla dimensione che userai e prova i controlli principali. Per il vetro usa anche contenuti chiari, scuri e dettagliati; per l'animazione controlla il movimento e l'eventuale chiusura del loop.

«Compilato» significa che il codice ha superato il controllo tecnico. «Verificato visivamente» richiede un'anteprima realmente ispezionata. Se questa manca, il risultato resta da verificare visivamente.

## 7. Migliora una cosa alla volta

```text
/REFINE [incolla l'ID reale dello shader]
Riduci l'iridescenza e rendi i riflessi meno saturi.
Mantieni identiche forme, distribuzione, trasparenza e distorsione.
```

Allega uno screenshot se vuoi correggere un difetto visivo. Per conservarne l'identità, indica ciò che deve rimanere invariato. La skill legge il sorgente corrente prima di modificarlo.

Per altri punti di partenza trovi cinque ricette nella cartella `shader-architect/examples`: vetro iridescente, cromo liquido, superficie olografica, distorsione organica e noise animato. Sono brief di progetto, non shader già compilati.
