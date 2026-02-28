# Option 2: Agentic AI Frameworks Using LLMs for Scientific/Computational Work

As of **February 28, 2026**, these are 5 recent and promising journal papers for the "agentic framework" direction (your preferred option).

## 1) Autonomous simulation workflow agent (high relevance)
- **Paper**: Liu et al., *Toward Automated Simulation Research Workflow through LLM Prompt Engineering Design*, **Journal of Chemical Information and Modeling** 65(1):114-124 (2025).
- **DOI**: https://doi.org/10.1021/acs.jcim.4c01653
- **Why interesting**: End-to-end autonomous simulation workflow (plan -> execute -> analyze -> report), close to your target of productivity in computational analysis.
- **Practical signal**: Demonstrates long-horizon simulation automation with iterative cycles.

## 2) Modular LLM agent for computational drug discovery
- **Paper**: *Large Language Model Agent for Modular Task Execution in Drug Discovery*, **Journal of Chemical Information and Modeling** (published Feb 9, 2026).
- **DOI**: https://doi.org/10.1021/acs.jcim.5c02454
- **Why interesting**: Strong modular multi-tool pattern (retrieval, prediction, refinement, structure generation) that can be transferred to CAE/FEM pipelines.
- **Practical signal**: Good reference architecture for tool-chaining and iterative agent loops.

## 3) LLM multi-agent extraction at materials scale
- **Paper**: Ghosh & Tewari, *LLM-based AI agents for automated extraction of material properties and structural features*, **Computational Materials Science** 265, 114521 (2026).
- **DOI**: https://doi.org/10.1016/j.commatsci.2026.114521
- **Why interesting**: Multi-agent pipeline turns large unstructured literature corpora into structured materials data; highly relevant for knowledge-grounded engineering agents.
- **Practical signal**: Shows agentic systems can produce machine-readable assets needed for downstream simulation/optimization loops.

## 4) Tool-using LLM agents in high-stakes domain
- **Paper**: Goodell et al., *Large language model agents can use tools to perform clinical calculations*, **npj Digital Medicine** 8, 163 (2025).
- **DOI**: https://doi.org/10.1038/s41746-025-01475-8
- **Why interesting**: Validates tool-use and delegated computation in high-stakes workflows; methodologically useful beyond medicine.
- **Practical signal**: Supports your idea that agent + tool orchestration is often more practical than "LLM-only reasoning".

## 5) Broad review of LLM agents in science
- **Paper**: Ramos, Collison, White, *A review of large language models and autonomous agents in chemistry*, **Chemical Science** 16, 2514-2572 (2025).
- **DOI**: https://doi.org/10.1039/D4SC03921A
- **Why interesting**: Comprehensive survey of agent architectures, tooling patterns, and limitations in science workflows.
- **Practical signal**: Useful as a map of design patterns before building your own agentic framework stack.

## Quick takeaway for your direction
- Option 2 is moving fast and is likely the faster path to impact in 1-2 years.
- Most promising near-term blueprint for computational analysis:
  1. LLM planner/reasoner
  2. strict tool APIs (solvers, meshing, post-processing, validators)
  3. self-check/retry loops
  4. provenance + evaluation harness
  5. human approval gates for critical runs

## Sources
- JCIM ASA paper: https://pubmed.ncbi.nlm.nih.gov/39801288/
- JCIM AgentD paper: https://doi.org/10.1021/acs.jcim.5c02454
- Computational Materials Science agent paper: https://doi.org/10.1016/j.commatsci.2026.114521
- npj Digital Medicine tool-use agents: https://doi.org/10.1038/s41746-025-01475-8
- Chemical Science review: https://doi.org/10.1039/D4SC03921A
