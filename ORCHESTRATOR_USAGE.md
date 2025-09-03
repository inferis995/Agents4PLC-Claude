# Come Usare l'Orchestrator Agent

## 🎯 Vantaggi dell'Orchestrator

- **Gestisce il workflow** - Ti dice esattamente cosa fare
- **Tracka il progresso** - Mostra dove sei nel processo
- **Fornisce prompt precisi** - Copy/paste diretto
- **Gestisce errori** - Sa come recuperare da fallimenti
- **Ottimizza il flusso** - Suggerisce miglioramenti

## 🚀 Come Iniziare

### Step 1: Lancia l'Orchestrator
```
Task Tool:
Subagent Type: general-purpose
Description: Agents4PLC Workflow Orchestrator

Prompt: [Copia da orchestrator_agent_prompt.md]
+ Aggiungi:
"
USER REQUIREMENT: Control LED with timer logic
CURRENT STATE: INIT  
PREVIOUS OUTPUT: None
"
```

### Step 2: Segui le Istruzioni
L'Orchestrator ti dirà:
- **Quale agente chiamare** (Retrieval/Planning/etc.)
- **Prompt esatto da usare** (copy/paste ready)
- **Cosa fare con l'output**
- **Prossimo step**

### Step 3: Aggiorna l'Orchestrator
Dopo ogni agente, ritorna dall'Orchestrator con:
```
USER REQUIREMENT: [stesso di prima]
CURRENT STATE: [nuovo stato: RETRIEVAL/PLANNING/etc.]
PREVIOUS OUTPUT: [output dall'agente appena eseguito]
```

## 🔄 Esempio Workflow Completo

### Round 1: Iniziare
**Input all'Orchestrator:**
```
USER REQUIREMENT: "Control conveyor belt with sensors"
CURRENT STATE: INIT
PREVIOUS OUTPUT: None
```

**Output dell'Orchestrator:**
```
CURRENT STATE: Starting RETRIEVAL phase
TASK INSTRUCTIONS: Use Retrieval Agent with this exact prompt...
NEXT STEPS: After Retrieval, return here with output for PLANNING phase
PROGRESS: [✓] Init → [ ] Retrieval → [ ] Planning → [ ] Coding → [ ] Validation
```

### Round 2: Dopo Retrieval
**Input all'Orchestrator:**
```  
USER REQUIREMENT: "Control conveyor belt with sensors"
CURRENT STATE: RETRIEVAL
PREVIOUS OUTPUT: [tutto l'output del Retrieval Agent]
```

**Output dell'Orchestrator:**
```
CURRENT STATE: Moving to PLANNING phase
TASK INSTRUCTIONS: Use Planning Agent with this prompt...
NEXT STEPS: Choose best plan and proceed to CODING
PROGRESS: [✓] Retrieval → [ ] Planning → [ ] Coding → [ ] Validation
```

## 🐛 Gestione Errori

Se validation fallisce:
```
USER REQUIREMENT: "Control conveyor belt with sensors"
CURRENT STATE: VALIDATION  
PREVIOUS OUTPUT: [errori di compilazione]
```

Orchestrator risponderà:
```
ERROR DETECTED: Syntax errors found
NEXT ACTION: Enter DEBUGGING phase
TASK INSTRUCTIONS: Use Debugging Agent with these errors...
ITERATION COUNT: 1/3 (max iterations before replanning)
```

## 🎛️ Controllo Granulare

**Puoi sempre:**
- Modificare i piani suggeriti
- Saltare step se hai già output
- Ripetere step con modifiche
- Cambiare requirement a metà processo

## 📊 Tracking Visuale

L'Orchestrator mantiene sempre:
```
WORKFLOW PROGRESS:
[✓] Retrieval: Found timer and conveyor patterns  
[✓] Planning: Generated 3 plans, selected Plan 2
[→] Coding: In progress...
[ ] Validation: Pending
[ ] Debugging: Not needed yet

CURRENT CONTEXT:
- Requirement: Conveyor with sensors
- Selected Plan: Plan 2 (Medium complexity)  
- Knowledge Base: Motor control + sensor patterns loaded
```

## 🚀 Pronto?

Lancia il tuo primo Orchestrator con qualsiasi richiesta PLC!