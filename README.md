# FIS 25-26: Pricing-Driven Self-Adaptation Experiment

## Overview

This repository contains the experimental setup for studying **Pricing-Driven Self-Adaptation** using the SPACE (Self-adaPtive Application based on Cost Estimation) technology. This experiment is designed for students to explore how software systems can automatically adapt their behavior based on pricing models and cost estimations.

## What is Pricing-Driven Self-Adaptation?

Pricing-Driven Self-Adaptation is a novel approach to self-adaptive systems where adaptation decisions are influenced by pricing models and cost considerations. Instead of relying solely on technical metrics (like response time or throughput), the system considers the economic impact of different configuration choices.

### Key Concepts

- **Self-Adaptation**: The ability of a system to automatically modify its behavior in response to changes in its environment or internal state
- **Pricing Models**: Economic frameworks that assign costs to different system configurations and resource usage patterns
- **Cost Estimation**: The process of predicting the financial impact of adaptation decisions
- **SPACE Technology**: Our Self-adaPtive Application framework that integrates cost estimation into the adaptation loop

## Objectives

The main objectives of this experiment are to:

1. **Understand Self-Adaptive Systems**: Learn the fundamental concepts of self-adaptation, including monitoring, analysis, planning, and execution (MAPE-K loop)

2. **Explore Pricing Models**: Investigate how different pricing strategies affect system behavior and adaptation decisions

3. **Evaluate Cost-Benefit Trade-offs**: Analyze how systems balance functional requirements with economic constraints

4. **Hands-on Experience with SPACE**: Gain practical experience implementing and configuring self-adaptive applications using our SPACE technology

5. **Experimental Analysis**: Design and conduct experiments to measure the effectiveness of pricing-driven adaptation strategies

## SPACE Technology

SPACE (Self-adaPtive Application based on Cost Estimation) is our framework for building self-adaptive systems that consider economic factors in their adaptation decisions.

### Architecture

SPACE follows the MAPE-K (Monitor, Analyze, Plan, Execute, Knowledge) reference model:

```
┌─────────────────────────────────────────┐
│            Knowledge Base               │
│  (Pricing Models, System Configuration) │
└─────────────────────────────────────────┘
         ▲                         ▲
         │                         │
    ┌────┴────┐               ┌───┴────┐
    │ Monitor │──────────────▶│ Analyze │
    └─────────┘               └────┬────┘
         ▲                         │
         │                         ▼
    ┌────┴────┐               ┌────────┐
    │ Execute │◀──────────────│  Plan  │
    └─────────┘               └────────┘
         │
         ▼
   ┌──────────┐
   │  System  │
   └──────────┘
```

### Key Features

- **Dynamic Pricing Integration**: Supports multiple pricing models (pay-per-use, tiered pricing, spot pricing)
- **Cost-Aware Planning**: Adaptation decisions consider both functional and economic objectives
- **SPHERE Integration**: Works seamlessly with SPHERE (Self-adaPtive arcHitecture based on Economic-driven Reconfiguration Engine)
- **Real-time Monitoring**: Continuous tracking of system performance and costs
- **Extensible Framework**: Easy to add new pricing models and adaptation strategies

### Getting Started with SPACE

#### Prerequisites

- Java 11 or higher
- Maven 3.6+
- Basic understanding of self-adaptive systems
- Familiarity with REST APIs

#### Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/Alex-GF/fis-25-26.git
   cd fis-25-26
   ```

2. Build the project (when available):
   ```bash
   mvn clean install
   ```

3. Configure your pricing model in `config/pricing-model.yaml`

4. Run the SPACE application:
   ```bash
   java -jar target/space-application.jar
   ```

#### Basic Usage

1. **Define Your Pricing Model**: Create a pricing configuration file that specifies costs for different resources and operations

2. **Configure Adaptation Rules**: Set up rules that define when and how the system should adapt based on cost thresholds

3. **Monitor System Behavior**: Use the built-in dashboard to observe adaptation decisions and their economic impact

4. **Analyze Results**: Export monitoring data for analysis and experimentation

#### Example Configuration

```yaml
pricing:
  model: pay-per-use
  resources:
    cpu:
      cost_per_hour: 0.05
    memory:
      cost_per_gb_hour: 0.01
    storage:
      cost_per_gb_month: 0.10
  
adaptation:
  cost_threshold: 10.0
  optimization_objective: minimize_cost
  constraints:
    max_response_time: 500ms
    min_availability: 99.5%
```

## SPHERE Technology

SPHERE (Self-adaPtive arcHitecture based on Economic-driven Reconfiguration Engine) is the architectural framework that complements SPACE. While SPACE focuses on the application-level adaptation logic, SPHERE provides the infrastructure and reconfiguration mechanisms.

### SPHERE Features

- **Dynamic Resource Allocation**: Automatically adjusts computing resources based on demand and cost
- **Service Selection**: Chooses between alternative service providers based on pricing and quality
- **Architectural Reconfiguration**: Modifies system architecture to optimize cost-performance trade-offs

## Experiment Guidelines

### For Students

1. **Review Documentation**: Start by reading this README and familiarizing yourself with the concepts
2. **Set Up Environment**: Follow the installation instructions
3. **Run Base Experiments**: Execute the provided example scenarios
4. **Design Your Experiments**: Create your own pricing models and adaptation strategies
5. **Analyze Results**: Document your findings and insights
6. **Report Issues**: Use the issue templates to ask questions or report problems

### Getting Help

If you encounter any issues or have questions during the experiment:

1. Check the existing issues to see if your question has been answered
2. Use the **Help Request** template for general questions about the experiment
3. Use the **Bug Report** template if you encounter technical problems
4. Tag your issues appropriately (SPACE, SPHERE, doubt, etc.)

## Contributing

This is an educational repository for the FIS 25-26 course. Students should:

- Report issues using the provided templates
- Ask questions tagged with `doubt`
- Suggest improvements tagged with `enhancement`
- Help identify bugs tagged with `bug`

## Labels Reference

- **SPACE**: Issues related to the SPACE framework
- **SPHERE**: Issues related to the SPHERE architecture
- **bug**: Something isn't working correctly
- **enhancement**: Suggestions for new features or improvements
- **documentation**: Improvements or additions to documentation
- **doubt**: Questions about concepts, usage, or experiments
- **duplicate**: This issue already exists

## Resources

Resources will be added as they become available:
- Course materials and additional documentation
- Research papers on pricing-driven self-adaptation
- API documentation for SPACE and SPHERE
- Video tutorials and walkthroughs

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For course-related questions, contact the teaching staff through the university platform.

For technical issues with the repository, please open an issue using the appropriate template.