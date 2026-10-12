# Knapsack Problem: Local Search Heuristics

## Overview
This notebook demonstrates and compares various local search-based metaheuristics for solving the 0/1 Knapsack Problem, comparing them against optimal solutions from Gurobi.

## Notebook Structure

### Section 1: Libraries and Setup
- Import necessary libraries
- Create output directories (`plots/`, `statistics/`, `results/`)

### Section 2: Configuration
- Set `max_instances` parameter (default: 10, full test: 1000)

### Section 3: Instance Management
- Functions to efficiently load instances one at a time
- Memory-efficient approach avoids loading all instances at once

### Section 4: Solution Encoding
- Binary vector representation
- Evaluation and feasibility checking functions

### Section 5: Initial Solution Generation
- Greedy constructive heuristic based on value-to-weight ratio

### Section 6: Neighborhood Generation
- Three neighborhood structures: 1-flip, 2-flip, swap

### Section 7: Gurobi Optimal Solver
- Baseline optimal solutions for comparison

### Section 8: Local Search Heuristics
- **Local Search (LS)**: Best and First Improvement strategies
- **Iterated Local Search (ILS)**: Perturbation-based diversification
- **Variable Neighborhood Search (VNS)**: Multiple neighborhood structures
- **Guided Local Search (GLS)**: Penalty-based objective modification

### Section 9: Visualization Functions
- Convergence plots comparing heuristics to optimal
- Statistics export to Excel

### Section 10: PHASE 1 - Gurobi Testing
- **All instances tested with Gurobi FIRST**
- Optimal solutions stored for comparison

### Section 11: PHASE 2 - Heuristic Testing
- Each instance loaded only when needed (memory efficient)
- All heuristics tested on each instance
- Convergence plot saved for each instance in `plots/`

### Section 12-13: Results Export
- Detailed statistics saved to `statistics/detailed_results.xlsx`
- Summary report saved to `results/summary_report.xlsx`

### Section 14: Comparative Analysis
- Average performance comparison (bar charts)
- Performance distribution (box plots)
- Quality vs. time trade-off (scatter plot)

### Section 15-16: Conclusions and Documentation
- Key findings and algorithm comparisons
- Output files summary

## Testing Modes

### Default Testing (Quick)
```python
max_instances = 10  # Tests 10 instances (2-3 minutes)
```

### Full Testing (Comprehensive)
```python
max_instances = 1000  # Tests all instances (much longer)
```

## Output Organization

### 📁 plots/
Individual convergence plots for each instance:
- `{instance_name}_convergence.png`
- Shows all heuristics vs optimal solution
- One plot per tested instance

### 📁 statistics/
Detailed Excel files:
- `detailed_results.xlsx` - Complete results table
  - Columns: Instance, Size, Capacity, Optimal_Value, Optimal_Time
  - For each heuristic: Value, Gap%, Time

### 📁 results/
Summary reports and aggregate visualizations:
- `summary_report.xlsx` - Aggregated statistics
- `average_performance_comparison.png` - Bar charts
- `performance_distribution.png` - Box plots
- `quality_vs_time_tradeoff.png` - Scatter plot

## Key Features

### Memory Efficiency
- Instances loaded **one at a time** during testing
- Garbage collection after each instance
- Prevents memory overflow with large datasets

### Testing Workflow
1. **Phase 1**: All instances tested with Gurobi (optimal solver)
2. **Phase 2**: All instances tested with each heuristic
3. Individual convergence plots generated for each instance
4. Results aggregated and exported

### Comprehensive Comparison
- Solution quality (objective value)
- Optimality gap (% from optimal)
- Computation time
- Convergence behavior

## Algorithms Tested

1. **Gurobi** - Optimal solver (baseline)
2. **LS-Best** - Local Search with Best Improvement
3. **LS-First** - Local Search with First Improvement
4. **ILS** - Iterated Local Search
5. **VNS** - Variable Neighborhood Search
6. **GLS** - Guided Local Search

## Requirements

```python
numpy
matplotlib
gurobipy
openpyxl
pandas
```

## Usage

1. Ensure `kp_instances/` directory contains instance files (.xlsx format)
2. Set `max_instances` in Section 2
3. Run all cells sequentially
4. Check output directories for results

## Notes

- Default configuration tests 10 instances for quick evaluation
- Set `max_instances = 1000` for comprehensive testing
- Each instance generates its own convergence plot
- All statistics automatically saved to Excel files
- Results organized in dedicated folders for easy access
