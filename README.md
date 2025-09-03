# 🏭 Agents4PLC - Multi-Agent Framework for Industrial PLC Code Generation

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Powered%20by-Claude%20Code-blue)](https://claude.ai/code)
[![IEC 61131-3](https://img.shields.io/badge/Standard-IEC%2061131--3-green)](https://www.iec.ch/)

A revolutionary multi-agent system that automates the generation and verification of **Structured Text (ST)** code for Programmable Logic Controllers (PLCs) using Claude Code's sub-agent architecture.

## 🚀 Features

- **🤖 Multi-Agent Architecture**: 5 specialized agents + 1 orchestrator working together
- **📚 Industrial Knowledge Base**: Validated examples from water treatment, manufacturing, and process control
- **🔍 Automatic Code Verification**: Syntax checking and formal verification integration
- **🛡️ Safety-First Design**: Industrial safety patterns and emergency shutdown procedures
- **📖 OSCAT Integration**: Industry-standard function blocks and control patterns
- **🎯 Real-World Validation**: Based on production-ready industrial systems

## 🏗️ Architecture

### Orchestrator Agent
Manages the complete workflow and guides users through the multi-agent process.

### Specialized Agents

1. **🔍 Retrieval Agent**: Searches industrial knowledge base for relevant PLC patterns
2. **📋 Planning Agent**: Generates structured implementation plans (simple to complex)
3. **⚙️ Coding Agent**: Generates high-quality ST code with RAG support
4. **🐛 Debugging Agent**: Fixes syntax and semantic errors using Chain-of-Thought
5. **✅ Validation Agent**: Compiles and formally verifies code correctness

## 📁 Project Structure

```
Agents4PLC/
├── datasets/
│   ├── plc_knowledge.md              # Basic PLC programming patterns
│   ├── st_code_examples.md           # Simple control examples
│   ├── industrial_water_treatment.md # Water/wastewater systems
│   ├── manufacturing_process_control.md # Production line control
│   └── oscat_function_blocks.md      # OSCAT library patterns
├── agent_prompts/
│   ├── orchestrator_agent_prompt.md  # Workflow management
│   ├── retrieval_agent_prompt.md     # Knowledge retrieval
│   ├── planning_agent_prompt.md      # Implementation planning
│   ├── coding_agent_prompt.md        # ST code generation
│   ├── debugging_agent_prompt.md     # Error fixing with CoT
│   └── validation_agent_prompt.md    # Code verification
├── examples/
│   ├── simple_led_control.md         # Basic examples
│   ├── complex_manufacturing.md      # Advanced systems
│   └── safety_critical_systems.md    # Emergency procedures
├── docs/
│   ├── USAGE_GUIDE.md                # Detailed usage instructions
│   ├── AGENT_ARCHITECTURE.md         # Technical architecture
│   └── CONTRIBUTING.md               # Contribution guidelines
├── LICENSE
└── README.md
```

## 🎯 Quick Start

### Prerequisites
- [Claude Code](https://claude.ai/code) access
- Basic understanding of PLC programming concepts

### Step 1: Clone the Repository
```bash
git clone https://github.com/your-username/Agents4PLC.git
cd Agents4PLC
```

### Step 2: Create Your Agents with `/agent`
1. Open Claude Code
2. Create the **Orchestrator Agent**:
   ```
   /agent create orchestrator "Agents4PLC Workflow Orchestrator"
   ```

3. Train it with the prompt from `agent_prompts/orchestrator_agent_prompt.md`:
   ```
   /agent train orchestrator
   ```
   Then paste the complete orchestrator prompt

4. Create all 5 specialized agents:
   ```
   /agent create retrieval "PLC Knowledge Retrieval Agent"
   /agent create planning "PLC Implementation Planning Agent" 
   /agent create coding "ST Code Generation Agent"
   /agent create debugging "ST Code Debugging Agent"
   /agent create validation "ST Code Validation Agent"
   ```

5. Train each agent with their respective prompts from `agent_prompts/`

### Step 3: Use the Workflow
Once agents are created and trained:

1. **Start with Orchestrator**:
   ```
   @orchestrator "Control LED with timer logic"
   ```

2. **Follow the guided workflow**:
   - Orchestrator tells you which agent to use next
   - Use `@retrieval`, `@planning`, `@coding`, `@validation`, `@debugging` 
   - Each agent provides input for the next step

3. **Example workflow**:
   ```
   @orchestrator "Create water treatment system"
   @retrieval [search for water treatment patterns]
   @planning [generate implementation plans]
   @coding [create ST code from selected plan]
   @validation [verify and compile code]
   ```

## 💡 Example Usage

### Simple LED Control
**Input**: `"Control LED with 5-second timer"`

**Generated ST Code**:
```st
PROGRAM LED_Timer_Control
VAR
    led_timer: TON;
    led_output: BOOL := FALSE;
    start_button: BOOL := FALSE;
END_VAR

led_timer(IN := start_button, PT := T#5s);
led_output := led_timer.Q;

END_PROGRAM
```

### Complex Industrial System
**Input**: `"Water treatment plant with chemical dosing and safety interlocks"`

**Result**: Complete multi-program ST code with:
- Chemical feed control with safety interlocks
- Multi-pump lead/lag operation
- Emergency shutdown procedures
- Formal verification properties

## 🏭 Industrial Applications

### Validated Control Systems
- **Water Treatment Plants**: Chemical dosing, filtration, disinfection
- **Manufacturing Lines**: 6-station production with quality control
- **Material Handling**: ASRS, AGV fleet management, inventory tracking
- **Process Control**: Temperature, pressure, flow control with PID
- **Safety Systems**: Emergency stops, gas leak detection, failsafe operation

### OSCAT Function Block Integration
- Advanced PID controllers with anti-windup
- Multi-pump lead/lag control systems
- Batch sequence controllers
- Analog input processing and scaling
- Temperature control with heating/cooling

## 🤝 Contributing

We welcome contributions from the industrial automation community!

### Ways to Contribute
- 🏭 **Add Industrial Examples**: Share validated PLC projects
- 🧠 **Improve Agent Prompts**: Enhance agent capabilities
- 📚 **Expand Knowledge Base**: Add new control patterns
- 🐛 **Report Issues**: Help improve code quality
- 📖 **Documentation**: Improve guides and examples

### Getting Started
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-industrial-system`)
3. Add your validated industrial examples to appropriate dataset files
4. Test with the agents to ensure proper generation
5. Submit a pull request

See [CONTRIBUTING.md](docs/CONTRIBUTING.md) for detailed guidelines.

## 📖 Documentation

- **[Usage Guide](docs/USAGE_GUIDE.md)**: Complete step-by-step instructions
- **[Agent Architecture](docs/AGENT_ARCHITECTURE.md)**: Technical implementation details
- **[Industrial Patterns](docs/INDUSTRIAL_PATTERNS.md)**: Explanation of control patterns used

## 🛡️ Safety Notice

This framework generates industrial control code. Always:
- **Review generated code** thoroughly before deployment
- **Test in simulation** environments first
- **Follow industrial safety standards** (IEC 61508, IEC 61511)
- **Implement proper safety interlocks** and emergency procedures
- **Validate with qualified automation engineers**

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Claude Code Team** at Anthropic for the sub-agent framework
- **OpenPLC Community** for open-source PLC runtime validation
- **OSCAT Library** for industrial function block patterns
- **IEC 61131-3 Standard** for Structured Text specification
- **Industrial Automation Community** for sharing validated control patterns

## 🌟 Star History

If this project helps you with PLC development, please consider giving it a star! ⭐

## 📞 Support

- **Issues**: Report bugs and request features via GitHub Issues
- **Discussions**: Join community discussions in GitHub Discussions
- **Documentation**: Check the docs/ folder for detailed guides

---

**Made with ❤️ by the industrial automation community**

*Powered by Claude Code - Automating Industrial Control System Development*