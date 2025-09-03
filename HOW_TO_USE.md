# Come Usare Agents4PLC in Claude Code

## Setup Completato ✅

Hai ora tutto il necessario per usare il framework Agents4PLC:

### 📁 Struttura Progetto
```
C:\Users\Utente\Agents4PLC\
├── datasets/
│   ├── plc_knowledge.md      # Database conoscenza PLC
│   └── st_code_examples.md   # Esempi codice ST  
├── agent_prompts/
│   ├── retrieval_agent_prompt.md
│   ├── planning_agent_prompt.md
│   ├── coding_agent_prompt.md
│   ├── debugging_agent_prompt.md
│   └── validation_agent_prompt.md
└── HOW_TO_USE.md (questo file)
```

## 🚀 Come Usare gli Agenti

### Step 1: Crea gli Agenti con `/agent`
```bash
# Crea l'Orchestrator
/agent create orchestrator "Agents4PLC Workflow Orchestrator"

# Crea tutti gli agenti specializzati
/agent create retrieval "PLC Knowledge Retrieval Agent"
/agent create planning "PLC Implementation Planning Agent"
/agent create coding "ST Code Generation Agent"
/agent create debugging "ST Code Debugging Agent"
/agent create validation "ST Code Validation Agent"
```

### Step 2: Addestra ogni Agente
```bash
# Addestra l'orchestrator
/agent train orchestrator
# Poi copia il prompt da agent_prompts/orchestrator_agent_prompt.md

# Addestra retrieval agent
/agent train retrieval  
# Poi copia il prompt da agent_prompts/retrieval_agent_prompt.md

# E così via per tutti gli agenti...
```

### Step 3: Usa il Workflow
```bash
# Inizia sempre con l'orchestrator
@orchestrator "Control LED with timer logic"

# Segui le istruzioni dell'orchestrator, esempio:
@retrieval "Cerca pattern per LED e timer"
@planning "Genera piani basati sui risultati del retrieval"
@coding "Genera codice ST dal piano selezionato"
@validation "Verifica il codice generato"
# @debugging "Correggi errori se necessario"
```

## 🔄 Workflow Completo

1. **Richiesta utente**: "Control LED with timer logic"
2. **Retrieval**: Cerca info nei datasets
3. **Planning**: Genera 3 piani implementazione  
4. **Coding**: Genera codice ST dal piano scelto
5. **Validation**: Compila e verifica codice
6. **Debugging**: (se errori) Corregge il codice
7. **Output**: Codice ST verificato e funzionante

## 📝 Esempio Pratico

**Input**: "Create traffic light control system"

**Retrieval Agent Output**: 
- Timer patterns (TON, TOF)
- State machine examples  
- Traffic light code da datasets

**Planning Agent Output**:
- Piano 1: Semplice (3 LED + timers)
- Piano 2: Con pulsante pedonale
- Piano 3: Controllo intelligente

**Coding Agent Output**: 
```st
PROGRAM Traffic_Light_Control
VAR
    red_timer: TON;
    green_timer: TON;
    yellow_timer: TON;
    // ... resto del codice
END_VAR
```

## 🎯 Vantaggi

- **Modulare**: Ogni agente ha un compito specifico
- **Riutilizzabile**: I prompt funzionano per qualsiasi requisito PLC
- **Estendibile**: Aggiungi facilmente nuovi datasets
- **Verificabile**: Codice validato formalmente

## 🛠 Personalizzazione

### Aggiungere Nuova Conoscenza:
1. Modifica `datasets/plc_knowledge.md`
2. Aggiungi esempi in `datasets/st_code_examples.md`

### Modificare Prompts:
1. Edita file in `agent_prompts/`  
2. Adatta per casi d'uso specifici

Ora puoi iniziare a usare Agents4PLC! 🎉