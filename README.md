# CrisisPath DSL

A Domain Specific Language for Crisis Modeling, Simulation, and Optimization.

## Features

- **Multiple Configuration Formats**: Support for YAML, JSON, TOML, HCL, Starlark, XML, and a custom DSL
- **Crisis Scenario Simulation**: Model complex crisis scenarios with cascading effects
- **Optimization Algorithms**: A* pathfinding and genetic algorithms for strategy optimization
- **Bottleneck Analysis**: Identify and analyze system vulnerabilities
- **Query Language**: Powerful query system for scenario exploration
- **Visualization Tools**: Timeline, network, and graph visualizations
- **Extensible Architecture**: Plugin system for custom extensions

## Installation

```bash
pip install crisispath-dsl
```

## Quick Start

```python
from crisispath import CrisisScenarioEngine, ConfigLoader

# Load configuration
config = ConfigLoader.load("scenario.yaml")

# Create and run simulation
engine = CrisisScenarioEngine(config)
result = engine.simulate_crisis("PowerBlackout", duration=72)

# Find optimal survival path
path = engine.find_optimal_survival_path(
    actor="FamilyWithKids",
    crisis="PowerBlackout",
    goals=[
        {"type": "has", "resource": "food", "amount": 7, "unit": "days"},
        {"type": "has", "resource": "water", "amount": 21, "unit": "liters"}
    ]
)

# Optimize strategy portfolio
portfolio = engine.optimize_strategy_portfolio(
    constraints={"budget": 1000, "time_limit": 30},
    objectives=["maximize_survival", "minimize_cost"]
)
```

## Configuration Examples

### YAML Format
```yaml
version: "1.0"

actors:
  - !actor
    name: "FamilyWithKids"
    resources:
      - name: water
        quantity: 20
        unit: liters
        critical: true

crises:
  - !crisis
    name: "PowerBlackout"
    triggers: ["grid_failure", "cyberattack"]
    effects:
      - type: eliminate
        target: electricity
```

### Simple DSL Format
```
# Define actors
actor FamilyWithKids:
  resource water 20L critical
  resource food 7days critical

# Define crises
crisis PowerBlackout:
  trigger grid_failure
  trigger cyberattack
  effect eliminate electricity
```

## CLI Usage

```bash
# Run simulation
crisispath simulate scenario.yaml --duration 72

# Analyze bottlenecks
crisispath analyze scenario.yaml --actor FamilyWithKids

# Optimize strategies
crisispath optimize scenario.yaml --objectives survival,cost

# Convert between formats
crisispath convert input.yaml output.toml

# Validate configuration
crisispath validate scenario.yaml
```

## Documentation

Full documentation is available at [https://crisispath-dsl.readthedocs.io](https://crisispath-dsl.readthedocs.io)

## Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Citation

If you use CrisisPath DSL in your research, please cite:

```bibtex
@software{crisispath2025,
  title = {CrisisPath DSL: A Domain Specific Language for Crisis Modeling},
  year = {2025},
  publisher = {Tom Sapletta},
  url = {https://github.com/apidsl/crisispath-dsl}
}
```
