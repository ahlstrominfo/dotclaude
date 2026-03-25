# Interface Design Agent Instructions

When designing interfaces for a deepened module, spawn 3+ sub-agents
in parallel. Each must produce a radically different interface.

## Agent constraints

Give each agent a different design constraint:
- Agent 1: "Minimize the interface — aim for 1-3 entry points max"
- Agent 2: "Maximize flexibility — support many use cases"
- Agent 3: "Optimize for the most common caller — make the default
  case trivial"
- Agent 4 (if applicable): "Design around the ports & adapters
  pattern for cross-boundary dependencies"

## Required output per agent

1. Interface signature (types, methods, params)
2. Usage example showing how callers use it
3. What complexity it hides internally
4. Dependency strategy
5. Trade-offs

## After collecting results

Present designs sequentially, then compare in prose.

Give your own recommendation: which design you think is strongest
and why. If elements from different designs would combine well,
propose a hybrid. Be opinionated.
