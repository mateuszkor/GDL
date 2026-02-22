# Research Proposal

**Project:** Exploratory Paper Analysis  
**Paper:** *Why Does Your Graph Neural Network Fail on Some Graphs? Insights from Exact Generalisation Error* (2025)

## 1) Goal
Produce a coherent backward-thinking and forward-thinking analysis grounded in evidence from the paper, plus a conceptual notebook plan to empirically probe the paper’s core claims.

## 2) Scope
- Literature-based analysis (no new theoretical derivations).
- Forward-thinking proposal: **Predictive Model Auditing** (conceptual).
- Notebook: design only (experiments described but not coded yet).
- Dataset downloads are allowed later.

## 3) Core Research Questions
1. Why do architectural explanations fail to predict GNN success across graph families?
2. How does exact generalisation error explain failure conditions?
3. Which graph-structural factors are most predictive of failure?
4. How can these factors drive a pre-training “audit” pipeline?

## 4) Evidence Table (Claims → Evidence → Implication)

1. **Architectural explanations are incomplete.**  
   Evidence: Abstract states over-smoothing/over-squashing don’t explain why similar architectures behave differently.  
   Implication: failure requires a different explanatory lens.

2. **Existing generalisation bounds are too loose or narrow.**  
   Evidence: Abstract notes prior bounds are loose, architecture-specific, and give limited insight.  
   Implication: need tighter, more general theory.

3. **Exact generalisation error is derived in a signal-processing view.**  
   Evidence: Abstract + Section 3 derive exact generalisation error in a fixed-design transductive setting.  
   Implication: theoretical grounding for failure prediction.

4. **Only aligned information between graph structure and features contributes to generalisation.**  
   Evidence: Abstract + Section 3 discussion.  
   Implication: misalignment explains failure even with “good” architectures.

5. **Misalignment can break even shallow GNNs.**  
   Evidence: Section 4.1 defines misalignment and shows failures with one-layer convolution.  
   Implication: depth/oversmoothing is not the only culprit.

6. **Heterophily degrades generalisation via spectral properties.**  
   Evidence: Section 4.2 models homophily/heterophily with a spectral signal.  
   Implication: graph family properties predict failure risk.

7. **Attention-based models can miss information under repeating eigenvalues.**  
   Evidence: Section 4.3 compares GAT vs Specformer with spectral filters.  
   Implication: some failures are inherent to model spectral sensitivity.

8. **Benchmark bias favors alignment and hides failures.**  
   Evidence: Conclusion notes CSBM and common benchmarks assume alignment.  
   Implication: failure can be systematic but under-reported.

## 5) Backward-Thinking Outline (2 pages)
1. **Problem setting:** GNN success is inconsistent across graph families.
2. **Historical explanations:** over-smoothing, over-squashing, expressivity limits.
3. **Gap:** architectural stories don’t predict why similar models diverge.
4. **Paper’s reframing:** exact generalisation error via signal processing.
5. **Evidence of failure mechanisms:**
   - Misalignment (graph–feature–label mismatch)
   - Heterophily as high-frequency label signals
   - Attention limits under repeating eigenvalues
6. **Synthesis:** failure is driven by structural alignment and spectrum, not just architecture.

## 6) Forward-Thinking Outline (2 pages)

**Predictive Model Auditing (conceptual proposal)**
1. **Audit stage:** compute a failure risk score from graph structure + alignment proxies.
2. **Decision stage:** recommend architecture choice or data transformation (rewiring/filtering).
3. **Validation stage:** test predicted risk across graph families; verify alignment with observed failures.

**Why this follows naturally:**
- Exact generalisation error provides a principled signal for pre-training risk estimation.
- Structural properties can be computed before training, enabling a pre-flight check.

**Near-term roadmap (conceptual):**
- Build a graph-family stress suite (homophily sweep, spectral gap, degree regimes).
- Calibrate risk score on benchmark datasets.
- Evaluate mitigations as part of the audit.

## 7) Conceptual Notebook Plan (No code yet)

**A) Graph families**
- Synthetic: SBM variants, homophily/heterophily sweep, degree distribution changes, spectral gap variation, repeating eigenvalues.
- Real datasets later (allowed).

**B) Models to compare**
- MLP baseline (no graph)
- GCN, GraphSAGE, GAT

**C) Structural risk signals**
- Homophily/heterophily metrics
- Spectral properties (eigenvalue distribution, spectral gap)
- Feature–label alignment proxies

**D) Evaluation protocol**
- Standard train/val/test splits per family
- Measure generalisation error and performance variance
- Correlate performance with structural risk signals

**E) Outputs**
- Table: model performance vs graph family
- Plot: performance vs homophily/alignment
- Heatmap: failure risk across graph property grid
- Summary: which model families degrade fastest and why

## 8) Out of Scope (for now)
- LaTeX drafting
- Running experiments
- Writing code

## 9) Acceptance Criteria
- Single coherent narrative connecting backward → forward.
- Every key point tied to paper evidence.
- Notebook plan is specific enough to implement later.
