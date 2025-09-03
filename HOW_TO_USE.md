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

### Step 1: Retrieval Agent
```
Usa Task tool con:
Subagent Type: general-purpose
Description: PLC Knowledge Retrieval Agent

Prompt: [Copia da agent_prompts/retrieval_agent_prompt.md]
+ Aggiungi: "USER REQUIREMENT: Control LED with timer logic"
```

### Step 2: Planning Agent  
```
Usa Task tool con:
Subagent Type: general-purpose
Description: PLC Implementation Planning Agent

Prompt: [Copia da agent_prompts/planning_agent_prompt.md]
+ Aggiungi: "INPUT: [output dal Retrieval Agent]"
```

### Step 3: Coding Agent
```
Usa Task tool con:
Subagent Type: general-purpose  
Description: ST Code Generation Agent

Prompt: [Copia da agent_prompts/coding_agent_prompt.md]
+ Aggiungi: "SELECTED PLAN: [piano dal Planning Agent]"
```

### Step 4: Validation Agent
```
Usa Task tool con:
Subagent Type: general-purpose
Description: ST Code Validation Agent  

Prompt: [Copia da agent_prompts/validation_agent_prompt.md]
+ Aggiungi: "ST CODE: [codice dal Coding Agent]"
```

### Step 5: Debugging Agent (se necessario)
```
Usa Task tool con:
Subagent Type: general-purpose
Description: ST Code Debugging Agent

Prompt: [Copia da agent_prompts/debugging_agent_prompt.md]  
+ Aggiungi: "ERRORS: [errori dal Validation Agent]"
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