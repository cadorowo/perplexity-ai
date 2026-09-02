# 🧠 Guida & Mappatura dei Modelli Perplexity AI (Frontier 2026)

Questo documento contiene il confronto, i benchmark e la mappatura completa dei modelli disponibili su Perplexity (Piani Pro & Max).

---

## 🏆 Classifica Globale: Qual è il Migliore?

Dall'analisi dei benchmark indipendenti e dei test sul campo:

### 1. 🥇 Miglior Modello in Assoluto (Coding, Ingegneria Software & Scrittura)
* **`Claude Sonnet 5`** (Anthropic) — *Disponibile su: Pro & Max*
  * **Parametro:** `mode="pro"`, `model="claude sonnet 5"` (Backend: `claude45sonnet` / `claude45sonnetthinking`)
  * **Perché è il #1:** È il modello di riferimento mondiale per **in-repository coding**, affidabilità tecnica ("follow-through") e assenza di allucinazioni. Supporta il reasoning adattivo su più livelli di sforzo.

### 2. 🥈 Miglior Modello OpenAI per Efficienza & Terminal Workflows
* **`GPT-5.6 Terra`** (OpenAI) — *Disponibile su: Pro & Max*
  * **Parametro:** `mode="pro"`, `model="gpt-5.2"` / `"gpt5"` (Backend: `gpt52` / `gpt52_thinking`)
  * **Perché:** Ottimizzato per compiti a riga di comando (CLI/terminale), risoluzione problemi a passi rapidi e alta efficienza di calcolo.

### 3. 🥉 Miglior Modello per Contesto Enorme (1M Token) & Ragionamento Astratto
* **`Gemini 3.1 Pro`** (Google) — *Disponibile su: Pro & Max*
  * **Parametro:** `mode="pro"`, `model="gemini-3.0-pro"` (Backend: `gemini30pro`)
  * **Perché:** Dominatore sui benchmark di ragionamento astratto (ARC-AGI-2), architettura MoE avanzata con sistema di "three-tier thinking" e capacità di analizzare interi codebase in un solo passaggio.

### 4. 🚀 Specialisti in Agentic Coding & STEM
* **`Grok 4.5`** (xAI): Modello MoE sviluppato con focus su compiti STEM e ingegneria agentica.
* **`Kimi K3`** (Moonshot AI): Modello da 2.8T di parametri con Kimi Delta Attention e "Agent Swarm" per task multi-step complessi.
* **`Nemotron 3 Ultra`** (NVIDIA): Architettura ibrida Transformer-Mamba da 550B creata da NVIDIA per reasoning avanzato e agenti autonomi.

### 5. 💎 Modelli Esclusivi Piano Max (Top di Gamma Assoluti)
* **`Claude Opus 5`** (Anthropic) & **`GPT-5.6 Sol`** (OpenAI):
  * *Disponibili esclusivamente per abbonati Perplexity Max.*
  * Riservati alla risoluzione di problemi scientifici e architetturali di complessità estrema.

---

## 📊 Tabella Comparativa Ufficiale (Pro vs Max)

| Modello | Fornitore | Piano Pro | Piano Max | Ragionamento | Mappatura Parametro |
| :--- | :--- | :---: | :---: | :--- | :--- |
| **Claude Sonnet 5** | Anthropic | **Sì** | **Sì** | Facoltativo | `model="claude sonnet 5"` |
| **GPT-5.6 Terra** | OpenAI | **Sì** | **Sì** | Facoltativo | `model="gpt-5.2"` / `"gpt-4.5"` |
| **Gemini 3.1 Pro** | Google | **Sì** | **Sì** | Sempre attivo | `model="gemini-3.0-pro"` |
| **Grok 4.5** | xAI | **Sì** | **Sì** | Facoltativo | `model="grok-4.1"` |
| **Kimi K3** | Moonshot AI | **Sì** | **Sì** | Sempre attivo | `model="kimi k3"` |
| **GLM 5.2** | Z.ai | **Sì** | **Sì** | Sempre attivo | `model="glm 5.2"` |
| **Nemotron 3 Ultra** | NVIDIA | **Sì** | **Sì** | Sempre attivo | `model="nemotron"` |
| **Sonar 2** | Perplexity | **Sì** | **Sì** | Non disponibile | `model="sonar"` |
| **Claude Opus 5** | Anthropic | ❌ No | **Sì** | Facoltativo | `model="claude opus 5"` (Solo Max) |
| **GPT-5.6 Sol** | OpenAI | ❌ No | **Sì** | Facoltativo | `model="gpt-5.6 sol"` (Solo Max) |

---

## 🎯 Modelli Principali in Uso (Default Duo)

Per le nostre attività attuali e di workflow, utilizziamo come modelli primari:
1. **`Claude Sonnet 5`** (`model="claude sonnet 5"`): Il modello di punta per coding, refactoring, architettura, sintesi e **video-workflow con reasoning**.
2. **`Kimi K3`** (`model="kimi k3"`): Modello con reasoning sempre attivo, eccellente per elaborazioni estese a lungo termine e task agentici multi-step.

---

## 🎬 Regola di Progetto: Video-Workflow (Reasoning Obbligatorio)

Per tutte le elaborazioni, pipeline e task relativi a **`video-workflow`** (es. storyboard, automazione video, script per video, pipeline di montaggio/rendering, timing e cue-points), è stabilito l'uso **obbligatorio della modalità `reasoning`** con **Claude Sonnet 5** (o **Gemini 3.1 Pro** per contesti molto estesi).

### Configurazione Standard per Video-Workflow:
* **Modalità:** `mode="reasoning"`
* **Modello:** `model="claude sonnet 5"`

```python
import json
import perplexity

with open("cookies.json", "r") as f:
    cookies = json.load(f)

client = perplexity.Client(cookies=cookies)

# Query Video-Workflow con Reasoning attivo
response = client.search(
    query="Progetta la pipeline di generazione video automatica con timing dei sottotitoli e cue audio",
    mode="reasoning",
    model="claude sonnet 5"
)
print(response["answer"])
```

---

## 📁 Supporto per Perplexity Projects / Spaces / Collections

È possibile indirizzare le ricerche all'interno di uno specifico **Project / Space / Collection** di Perplexity passando il parametro `collection_uuid`.

In questo modo la query eredita le istruzioni personalizzate del Project e accede ai file/documenti caricati al suo interno.

### Come recuperare il `collection_uuid`:
Apri il tuo Project/Space su Perplexity nel browser: l'URL sarà nella forma `https://www.perplexity.ai/spaces/<UUID>` oppure `https://www.perplexity.ai/collections/<UUID>`. Copia la stringa UUID.

### Esempio di utilizzo:
```python
import json
import perplexity

with open("cookies.json", "r") as f:
    cookies = json.load(f)

client = perplexity.Client(cookies=cookies)

response = client.search(
    query="Quali sono le conclusioni principali nei documenti di questo progetto?",
    mode="pro",
    model="claude sonnet 5",
    collection_uuid="12345678-abcd-1234-abcd-1234567890ab"
)

print(response["answer"])
```
