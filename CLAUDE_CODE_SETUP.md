# 🤖 Claude Code Setup Guide for Agents4PLC

## 📋 Complete Setup Instructions

### Step 1: Create All Agents

Use the `/agent create` command to create each agent:

```bash
# Create the Orchestrator Agent
/agent create orchestrator "Agents4PLC Workflow Orchestrator"

# Create the 5 Core Agents
/agent create retrieval "PLC Knowledge Retrieval Agent"
/agent create planning "PLC Implementation Planning Agent"
/agent create coding "ST Code Generation Agent" 
/agent create debugging "ST Code Debugging Agent"
/agent create validation "ST Code Validation Agent"
```

### Step 2: Train Each Agent

#### 1. Train Orchestrator Agent
```bash
/agent train orchestrator
```
Then copy-paste the complete prompt from `agent_prompts/orchestrator_agent_prompt.md`

#### 2. Train Retrieval Agent  
```bash
/agent train retrieval
```
Copy-paste from `agent_prompts/retrieval_agent_prompt.md`

#### 3. Train Planning Agent
```bash
/agent train planning  
```
Copy-paste from `agent_prompts/planning_agent_prompt.md`

#### 4. Train Coding Agent
```bash
/agent train coding
```
Copy-paste from `agent_prompts/coding_agent_prompt.md`

#### 5. Train Debugging Agent
```bash
/agent train debugging
```
Copy-paste from `agent_prompts/debugging_agent_prompt.md`

#### 6. Train Validation Agent
```bash
/agent train validation
```
Copy-paste from `agent_prompts/validation_agent_prompt.md`

## 🚀 Usage Workflow

### Quick Start Example

1. **Initialize with Orchestrator**:
```bash
@orchestrator "I want to control LED with timer logic"
```

2. **Follow the guided steps** (Orchestrator will tell you which agent to use):
```bash
@retrieval [follow orchestrator instructions]
@planning [with retrieval results]  
@coding [with selected plan]
@validation [with generated code]
# @debugging [only if validation finds errors]
```

### Complete Example Workflow

```bash
# Step 1: Start the process
@orchestrator "Create a water treatment plant control system with chemical dosing and safety interlocks"

# Step 2: Knowledge retrieval (orchestrator will guide you)
@retrieval "Find water treatment patterns with chemical dosing and safety systems"

# Step 3: Plan generation
@planning "Generate plans for water treatment system based on retrieved knowledge: [paste retrieval results]"

# Step 4: Code generation  
@coding "Generate ST code for Plan 2 (medium complexity): [paste selected plan details]"

# Step 5: Validation
@validation "Validate this ST code: [paste generated code]"

# Step 6: Debugging (if needed)
@debugging "Fix these compilation errors: [paste error details]"
```

## 🔧 Agent Management Commands

### List Your Agents
```bash
/agent list
```

### Check Agent Details
```bash
/agent info orchestrator
/agent info retrieval
# etc.
```

### Update Agent Training
```bash
/agent train [agent_name]
# Then provide updated/improved prompt
```

### Delete Agent (if needed)
```bash
/agent delete [agent_name]
```

## 💡 Usage Tips

### 1. **Always Start with Orchestrator**
The orchestrator manages the workflow and tells you exactly which agent to use next.

### 2. **Copy-Paste Between Agents**
Each agent output becomes input for the next agent. The orchestrator tells you exactly what to copy.

### 3. **Iterative Improvement** 
You can go back to any agent to improve results:
```bash
@planning "Generate alternative plan with more safety features"
@coding "Modify the code to add emergency shutdown logic"
```

### 4. **Agent Specialization**
Each agent is trained for specific tasks:
- **@orchestrator**: Workflow management
- **@retrieval**: Finding relevant PLC patterns
- **@planning**: Creating implementation strategies  
- **@coding**: Writing ST code
- **@debugging**: Fixing errors with Chain-of-Thought
- **@validation**: Checking syntax and logic

## 🏭 Real-World Examples

### Simple Control System
```bash
@orchestrator "Control a conveyor belt with start/stop buttons and emergency stop"
# Follow the guided workflow...
```

### Complex Industrial System
```bash
@orchestrator "Design a 6-station manufacturing line with quality control, AGV material handling, and safety interlocks"
# This will create a comprehensive multi-program system
```

### Safety-Critical Application
```bash  
@orchestrator "Create emergency shutdown system for chemical processing plant with gas leak detection"
# Focuses on safety-first design patterns
```

## 🔄 Troubleshooting

### Agent Not Working Properly?
1. **Retrain the agent** with updated prompt:
```bash
/agent train [agent_name]
```

2. **Check agent info**:
```bash
/agent info [agent_name]
```

### Getting Poor Results?
1. **Be more specific** in your requests
2. **Use the orchestrator** to guide the process  
3. **Iterate** - go back to previous agents to refine

### Workflow Confusion?
1. **Always start with @orchestrator**
2. **Follow the exact sequence** it provides
3. **Copy-paste outputs** between agents as instructed

## 📚 Knowledge Base Integration

The agents are trained to use the industrial knowledge base in `datasets/`:

- `plc_knowledge.md` - Basic PLC patterns
- `st_code_examples.md` - Simple examples  
- `industrial_water_treatment.md` - Water/wastewater systems
- `manufacturing_process_control.md` - Production lines
- `oscat_function_blocks.md` - OSCAT library patterns

Make sure these files are available for the agents to reference.

## ✅ Verification Checklist

After setup, verify your agents work:

- [ ] All 6 agents created successfully
- [ ] All agents trained with their specific prompts
- [ ] Orchestrator can guide the workflow
- [ ] Retrieval agent can find patterns from datasets
- [ ] Planning agent generates structured plans
- [ ] Coding agent creates valid ST code
- [ ] Validation agent checks syntax and logic
- [ ] Debugging agent can fix errors

## 🎯 Success Indicators

You'll know the setup is working when:
- Orchestrator provides clear workflow guidance
- Each agent produces relevant, high-quality output
- Generated ST code compiles correctly
- Industrial safety patterns are included automatically
- Complex systems are broken down into manageable components

---

**Ready to generate professional PLC code with AI agents? Start with the orchestrator! 🚀**

```bash
@orchestrator "What can you help me create today?"
```