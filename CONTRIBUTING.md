# Contributing to Agents4PLC

🎉 Thank you for your interest in contributing to Agents4PLC! This project thrives on community contributions from industrial automation professionals, PLC programmers, and AI enthusiasts.

## 🤝 Ways to Contribute

### 1. 🏭 Industrial Examples and Patterns
- **Validated PLC Projects**: Share real-world, tested industrial control systems
- **Control Patterns**: Add proven automation patterns from your industry experience
- **Safety Systems**: Contribute emergency shutdown and failsafe procedures
- **Industry-Specific Knowledge**: Water treatment, manufacturing, power generation, etc.

### 2. 🧠 Agent Improvements
- **Enhanced Prompts**: Improve agent prompt engineering for better code generation
- **New Agent Types**: Design specialized agents for specific industrial domains
- **Workflow Optimization**: Improve the multi-agent coordination process
- **Error Handling**: Better debugging and validation procedures

### 3. 📚 Knowledge Base Expansion
- **OSCAT Function Blocks**: Add more validated OSCAT library patterns
- **New Standards**: IEC 61499, PLCopen Safety, etc.
- **Documentation**: Improve explanations and examples
- **Translations**: Help make the project accessible globally

### 4. 🛠️ Technical Enhancements
- **Code Quality**: Improve ST code generation quality
- **Testing Framework**: Add automated testing for generated code
- **Integration**: Connect with PLC simulation tools
- **Performance**: Optimize agent response times

## 🚀 Getting Started

### Prerequisites
- Experience with PLC programming (Structured Text preferred)
- Understanding of industrial automation systems
- Familiarity with Claude Code or similar AI tools
- GitHub account for collaboration

### Development Setup
1. **Fork the Repository**
   ```bash
   git clone https://github.com/your-username/Agents4PLC.git
   cd Agents4PLC
   ```

2. **Create a Development Branch**
   ```bash
   git checkout -b feature/your-contribution-name
   ```

3. **Test Your Changes**
   - Use Claude Code to test agent prompts
   - Validate generated ST code with PLC simulation tools
   - Ensure examples work as expected

## 📋 Contribution Guidelines

### Industrial Example Submissions

When contributing industrial examples:

#### ✅ What We Want
- **Production-Tested Code**: Systems that have been validated in real industrial environments
- **Complete Documentation**: Clear explanations of system operation and safety procedures
- **Safety Compliance**: Code following industrial safety standards (IEC 61508, IEC 61511)
- **Realistic Scenarios**: Real-world problems and solutions
- **Multiple Complexity Levels**: Simple to advanced implementations

#### ❌ What to Avoid
- **Theoretical Examples**: Untested academic exercises
- **Incomplete Code**: Missing safety interlocks or error handling
- **Proprietary Information**: Company-specific or confidential implementations
- **Unsafe Practices**: Code that doesn't follow safety standards

### Code Quality Standards

#### ST Code Requirements
```st
// ✅ Good Example
PROGRAM Water_Pump_Control
VAR
    pump_run: BOOL := FALSE;
    pump_feedback: BOOL := FALSE;
    emergency_stop: BOOL := FALSE;
    start_button: BOOL := FALSE;
END_VAR

// Safety interlock - highest priority
IF emergency_stop THEN
    pump_run := FALSE;
ELSIF start_button AND NOT pump_feedback THEN
    pump_run := TRUE;
END_IF;

END_PROGRAM
```

#### Documentation Standards
- **Clear Purpose**: Explain what the system controls
- **Safety Notes**: Document all safety considerations
- **Operation Description**: How the system works
- **Testing Procedures**: How to validate the code
- **Real-World Context**: Where this would be used

### Agent Prompt Guidelines

When improving agent prompts:

#### Structure Requirements
```markdown
## Agent Configuration
**Subagent Type:** general-purpose
**Description:** [Clear, specific description]

## Prompt Template
[Detailed prompt with clear instructions]

## Usage Example
[Specific example of how to use the agent]
```

#### Quality Criteria
- **Specificity**: Clear, actionable instructions
- **Industrial Context**: Understanding of PLC programming needs
- **Error Handling**: Guidance for edge cases and failures
- **Safety Awareness**: Industrial safety considerations
- **Consistency**: Compatible with other agents in the framework

## 🔄 Submission Process

### 1. Create Your Contribution
- Add new files in appropriate directories
- Update existing files with improvements
- Include comprehensive documentation
- Test thoroughly with Claude Code

### 2. File Locations
```
datasets/               # Add industrial examples here
├── your_industry.md   # New industry-specific patterns
├── plc_knowledge.md   # Basic patterns (improvements)
└── ...

agent_prompts/          # Agent improvements
├── new_agent_prompt.md # New specialized agents
├── existing_agent.md  # Improvements to existing agents
└── ...

examples/              # Working examples
├── your_example.md    # Step-by-step examples
└── ...

docs/                  # Documentation
├── INDUSTRY_GUIDE.md  # Industry-specific guides
└── ...
```

### 3. Pull Request Process
1. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "Add: Water treatment control patterns with safety interlocks"
   ```

2. **Push to Your Fork**
   ```bash
   git push origin feature/your-contribution-name
   ```

3. **Create Pull Request**
   - Use descriptive title and clear description
   - Reference any related issues
   - Include testing results
   - Provide context about real-world usage

### 4. Pull Request Template
```markdown
## Description
Brief description of your contribution

## Type of Change
- [ ] New industrial examples
- [ ] Agent prompt improvements
- [ ] Documentation updates
- [ ] Bug fixes

## Industrial Context
- Industry: [Manufacturing/Water Treatment/Power/etc.]
- System Type: [Process Control/Safety System/etc.]
- Real-world Usage: [Brief description]

## Testing
- [ ] Tested with Claude Code agents
- [ ] Validated ST code syntax
- [ ] Confirmed safety procedures
- [ ] Reviewed by automation professionals

## Checklist
- [ ] Code follows project standards
- [ ] Documentation is complete
- [ ] Safety considerations addressed
- [ ] Examples are realistic and tested
```

## 📖 Documentation Standards

### README Updates
When adding new features:
- Update the main README.md
- Add your contribution to the feature list
- Include usage examples
- Update the project structure if needed

### Code Comments
```st
// ✅ Good Documentation
PROGRAM Chemical_Dosing_System
VAR
    // Safety interlocks
    emergency_stop: BOOL := FALSE;          // E-stop button input
    chemical_leak_detected: BOOL := FALSE;  // Gas detection system
    
    // Process variables
    ph_measurement: REAL := 7.0;            // pH sensor (4-20mA scaled)
    chemical_pump: BOOL := FALSE;           // Dosing pump output
    
    // Control parameters
    target_ph: REAL := 7.2;                // Process setpoint
    dosing_rate: REAL := 0.0;              // ml/min dosing rate
END_VAR

// SAFETY: Emergency shutdown takes precedence over all operations
IF emergency_stop OR chemical_leak_detected THEN
    chemical_pump := FALSE;
    dosing_rate := 0.0;
    // Activate emergency ventilation, shutdown procedures, etc.
ELSE
    // Normal pH control operation
    // ... control logic here
END_IF;

END_PROGRAM
```

## 🛡️ Safety and Quality Assurance

### Industrial Safety Requirements
All contributions must consider:

1. **Emergency Shutdown**: Every system must have safe shutdown procedures
2. **Fail-Safe Design**: Outputs must fail to safe states
3. **Interlock Verification**: Safety interlocks must be testable
4. **Alarm Management**: Critical alarms must be clearly defined
5. **Maintenance Mode**: Safe procedures for maintenance operations

### Code Review Process
1. **Technical Review**: ST syntax and logic validation
2. **Safety Review**: Industrial safety standard compliance
3. **Testing Verification**: Confirmation that examples work as described
4. **Documentation Review**: Completeness and clarity
5. **Community Feedback**: Input from other contributors

## 🏷️ Issue Reporting

### Bug Reports
When reporting bugs:
- **Agent Used**: Which agent had the issue
- **Input Provided**: Exact prompt or requirement given
- **Expected Output**: What should have happened
- **Actual Output**: What actually happened
- **Claude Code Version**: Version information if available

### Feature Requests
For new features:
- **Industrial Need**: Real-world problem this would solve
- **Proposed Solution**: How you envision it working
- **Alternative Approaches**: Other ways to solve the problem
- **Implementation Ideas**: Technical approach suggestions

## 🌍 Community

### Communication Channels
- **GitHub Issues**: Bug reports and feature requests
- **GitHub Discussions**: General discussions and questions
- **Pull Request Reviews**: Technical discussions on contributions

### Community Guidelines
- **Be Respectful**: Professional, constructive communication
- **Share Knowledge**: Help others learn from your expertise
- **Safety First**: Always prioritize industrial safety
- **Quality Focus**: Strive for production-ready contributions
- **Collaborative Spirit**: Work together to improve the framework

## 🎉 Recognition

### Contributor Types
- **🏭 Industrial Expert**: Shares real-world automation experience
- **🧠 AI Specialist**: Improves agent prompts and AI integration
- **📚 Documentation Guru**: Enhances project documentation
- **🛠️ Technical Developer**: Adds tools and integrations
- **🛡️ Safety Champion**: Focuses on industrial safety standards

### Hall of Fame
Outstanding contributors will be recognized in:
- Project README.md acknowledgments
- Contributor documentation
- GitHub contributor statistics

Thank you for helping make Agents4PLC a valuable resource for the industrial automation community! 🚀

---

**Questions?** Feel free to open a GitHub Discussion or reach out through Issues. The community is here to help!