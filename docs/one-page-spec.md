# Pseudo Structure Detection Model v0.1
## One-Page Specification

## 1. What this is

**Pseudo Structure Detection Model v0.1 (PSDM v0.1)** is a lightweight specification for detecting outputs that *look structurally coherent* but are weak in grounding, traceability, operational specificity, or evidential reliability.

In short:

> **It detects “structure-like outputs” that resemble real insight, while lacking enough real support beneath the surface.**

This model is not a truth machine and not a final judge of meaning.  
It is a **diagnostic framework** for identifying structural warning signs.

---

## 2. Why it exists

In AI-generated or human-written text, some outputs can appear:

- polished
- abstractly persuasive
- terminology-rich
- internally smooth
- emotionally or rhetorically convincing

…and yet still be structurally weak.

Typical weaknesses include:

- unclear evidence
- missing origin or trace
- circular restatement
- vague causality
- inflated abstraction without operational anchors
- authority-like tone without verifiable support

PSDM v0.1 is designed to detect these cases in a structured, repeatable way.

---

## 3. Core definition

A **pseudo-structure** is an output that presents the *appearance of structure* without sufficient grounding to justify that appearance.

This often means the text has one or more of the following traits:

- coherence without traceability
- abstraction without operational detail
- confidence without evidence
- explanation without causal anchoring
- novelty claims without comparison or proof
- structural language that does not actually resolve ambiguity

---

## 4. Primary detection dimensions

PSDM v0.1 evaluates outputs through a small set of structural risk dimensions.

### A. Trace Deficit
The output does not sufficiently show where its claims come from.

Examples:
- no source path
- no origin reference
- no evidence anchor
- no reproducible basis

### B. Operational Deficit
The output sounds insightful but cannot be acted on or implemented.

Examples:
- no concrete steps
- no measurable criteria
- no executable logic
- no clear decision rule

### C. Circular Framing
The output restates its claim using different wording rather than supporting it.

Examples:
- “This is important because it is structurally important”
- “It is valid because it is fundamentally valid”

### D. Authority Simulation
The output adopts a confident or expert-like posture without enough support.

Examples:
- “clearly,” “obviously,” “inevitable,” used without proof
- inflated certainty masking weak basis

### E. Semantic Density without Anchors
The output is rich in concepts but poor in verification points.

Examples:
- many abstract nouns
- few observable references
- high conceptual compression without unpacking

### F. Causal Ambiguity
The output implies mechanisms or consequences but does not show how they follow.

Examples:
- “this leads to…”
- “therefore society will…”
- “as a result the model becomes…”

without sufficient causal bridge

---

## 5. Minimal output model

A PSDM v0.1 evaluation should ideally produce:

- a target identifier
- an overall pseudo-structure score
- dimension-level findings
- evidence excerpts or reasons
- a recommended action

A minimal conceptual result looks like this:

```json
{
  "model": "PSDM-v0.1",
  "target_id": "sample-001",
  "pseudo_structure_score": 72,
  "risk_level": "high",
  "flags": [
    "trace_deficit",
    "operational_deficit",
    "authority_simulation"
  ],
  "summary": "The text appears coherent and confident, but lacks concrete evidence, traceable support, and executable detail.",
  "recommended_action": "request_evidence_or_rewrite"

6. Score interpretation

A simple interpretation range for v0.1:

0–24: low pseudo-structure risk
25–49: mild risk
50–74: moderate risk
75–100: high risk

These thresholds are heuristic, not absolute truth judgments.

7. Typical use cases

PSDM v0.1 can be used for:

AI output review
prompt engineering diagnostics
editorial review of abstract claims
governance pipelines for generated text
evaluation of “impressive but weakly grounded” writing
early-stage structural QA for spec-like documents
8. Non-goals

PSDM v0.1 does not try to:

determine universal truth
replace human judgment
measure literary beauty
reject abstraction itself
punish originality or philosophical writing

The model only asks:

Does this output have enough structural support for the confidence and coherence it displays?

9. Repository components

This repository includes:

README.md — project overview
yaml/ — YAML-based model definition
schema json/ — JSON Schema definition
sample json/ — example validation payloads
.github/workflows/validate-specs.yml — CI validation workflow
10. Version note

v0.1 is the initial public baseline.

It defines the first formal structure for detecting pseudo-structural outputs, with room for future expansion in:

scoring refinement
richer evidence typing
interoperability rules
multi-model evaluation
trace-aware reporting
}
