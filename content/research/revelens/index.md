---
title: "Revelens: AI-Powered Kubernetes Operations"
date: 2026-04-17T10:00:00-03:00
draft: false
description: "Phase 2 Completion: Optimization Scenarios for Proactive Kubernetes Performance Tuning"
---

## Revelens: From Reactive RCA to Proactive Optimization

Revelens is an AI-driven platform that revolutionizes how Site Reliability Engineers and DevOps teams manage Kubernetes at scale—moving beyond reactive root cause analysis into proactive performance optimization.

**Project Website:** [revelens.dev](https://revelens.dev)  
**GitHub Repository:** [revelens](https://github.com/your-org/revelens)

---

## 🚀 Phase 2 Completion: Optimization Scenarios Framework

### What's New

Beyond failure injection and RCA, Revelens now includes **optimization scenarios** that challenge LLMs to improve measurable KPIs in working-but-suboptimal deployments. This enables systematic evaluation of how well different LLMs reason about performance bottlenecks, apply targeted changes, and converge on SLA targets within bounded turn limits.

**Key Achievement:** Multi-turn optimization feedback loop where LLMs apply a change and immediately see its KPI impact, enabling iterative refinement.

### Architecture Highlights

- **Multi-Turn Feedback Loop**: LLMs apply optimizations, measure KPI impact, decide next steps—all in the same turn via `apply_kubectl_and_measure` tool
- **Scenario-Agnostic Visualization**: Generic visualization system adapts to any KPI type (latency, throughput, error rate, cost) by reading metric definitions from scenario metadata
- **Constraint Satisfaction**: Optimization must respect resource constraints (e.g., CPU limits, memory caps) while improving performance
- **Safe Remediation**: All kubectl commands validated against dangerous patterns before execution

### Initial Scenario: OPT-1 NRF SBI Latency

**Deployment:** Open5GS 5G Core  
**Problem:** NRF throttled to 50m CPU → cascading SBI latency across network functions  
**Objectives:**
- Reduce p99 SBI latency from baseline (~600ms) to < 100ms
- Keep error rate below 1%
- Maintain NRF CPU limit ≤ 500m

**Ground Truth Fix:** Increase NRF CPU limit from 50m to 250–500m

**Multi-Turn Example:**
```
Turn 1: Measure baseline KPIs → identify high p99 latency
Turn 2: Check resource usage → see NRF CPU at 100% (throttled)
Turn 3: Apply CPU limit increase → re-measure → verify SLA satisfaction
```

---

## 📊 Framework Components

### Optimization Engine
- Loads scenario YAML with objective function, KPI thresholds, and constraints
- Applies baseline manifests to inject suboptimal state
- Orchestrates multi-turn LLM loop with real-time KPI feedback
- Automatic visualization generation at completion

### KPI Tools
- **`measure_sbi_latency()`**: HTTP/2 SBI latency probes via kubectl exec, returns p50/p95/p99, error rate, constraint satisfaction
- **`apply_kubectl_and_measure()`**: Apply kubectl change, wait for rollout, measure KPIs in single turn
- **`get_nf_resource_usage()`**: Show configured limits and live kubectl top metrics

### Visualization
Fully generic plots adapt to scenario KPIs:
- **KPI Trajectories**: Per-metric line plots with threshold markers
- **Objective Timeline**: Step plot showing when objective became satisfied
- **Improvement Bars**: Baseline vs. final values per KPI
- **Model Comparison**: Grouped bars across multiple runs

---

## 🔧 Running Optimization Scenarios

### Prerequisites
```bash
cd revelens
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements_revelens.txt
export OPENROUTER_API_KEY="your-key"  # Set API key BEFORE running
kind create cluster
./scripts/llm/lib/deploy_open5gs.sh
```

### Execute Optimization
```bash
# Run with defaults
./scripts/llm/runners/run_llm_optimization.sh --scenario opt-1

# Override model and turn limit
./scripts/llm/runners/run_llm_optimization.sh \
  --scenario opt-1 \
  --llm-provider openrouter \
  --llm-model deepseek-ai/DeepSeek-V3.2-TEE \
  --max-turns 5
```

### Output
Results written to `evaluation/generated/optimization/<scenario-id>/<timestamp>/`:
- `optimization-result.json` — Complete session metadata, turn history, final KPIs
- `plots/` — Auto-generated KPI trajectory, improvement, and comparison visualizations

---

## 🎯 Research Questions

Optimization scenarios enable investigation of:

1. **Model Capability**: Which LLMs produce the most efficient optimization strategies?
2. **Turn Efficiency**: How many iterations does each model need to reach SLA?
3. **Constraint Awareness**: Do LLMs respect resource limits while optimizing?
4. **Reasoning Quality**: Can we extract interpretable optimization insights from LLM behavior?
5. **Cost-Performance Trade-offs**: How do models balance multiple conflicting objectives?

---

## 📚 Documentation

For comprehensive details, see:
- **README**: [github/revelens/README.md](https://github.com/your-org/revelens#optimization-scenarios)
- **Scenario Guide**: [docs/optimization-scenarios.md](https://github.com/your-org/revelens/blob/main/docs/optimization-scenarios.md)
- **Implementation Details**: [scripts/llm/engine/llm_optimization_engine.py](https://github.com/your-org/revelens/blob/main/scripts/llm/engine/llm_optimization_engine.py)

---

## 🗺️ Next Steps: Phase 3

- **Krkn-AI Integration**: Import community chaos scenarios and evaluate LLM performance
- **Multi-Metric Optimization**: Scenarios with competing objectives (latency vs. cost, throughput vs. memory)
- **Constraint Learning**: LLMs that learn and refine constraint awareness over multiple runs

---

## 📖 Related Research

This work builds on foundational research in:
- Multi-agent RL for resource optimization
- Distributed systems performance tuning
- LLM reasoning and planning in dynamic environments

---

**Contact:** INTRIG, FEEC-UNICAMP  
**Last Updated:** April 17, 2026
