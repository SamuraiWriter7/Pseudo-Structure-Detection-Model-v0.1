# Contributing to Pseudo Structure Detection Model v0.1

Thank you for your interest in contributing to this project.

This repository is a specification-oriented project for defining, validating, and evolving the **Pseudo Structure Detection Model (PSDM)**. Contributions are welcome when they improve clarity, consistency, validation reliability, or conceptual precision.

---

## Scope of contributions

Useful contributions include:

- improving wording in the README or one-page specification
- refining YAML or JSON Schema structure
- improving sample JSON examples
- fixing inconsistencies between documentation and schema
- strengthening validation workflow
- clarifying terminology or scoring logic
- proposing future-compatible extensions for later versions

This repository is **not** intended for vague expansion without structural justification.  
Please keep contributions aligned with the core purpose of the model.

---

## Guiding principles

When contributing, please preserve the following principles:

1. **Clarity over ornament**  
   Prefer precise structure over rhetorical complexity.

2. **Traceability over impression**  
   Definitions should be inspectable and, where possible, testable.

3. **Consistency over fragmentation**  
   README, YAML, JSON Schema, sample JSON, and CI should not contradict each other.

4. **Minimalism over unnecessary inflation**  
   Add only what improves the model’s structural usefulness.

5. **Version-aware thinking**  
   Changes that alter the meaning of the model should be treated as versioned changes, not silent edits.

---

## Before submitting changes

Please check the following before opening a pull request:

- The proposed change matches the repository’s conceptual scope
- Documentation and schema remain aligned
- Sample JSON still validates against the schema
- Naming is consistent across files
- The change improves structure rather than only increasing volume

If your proposal changes the model’s semantics, please explain:

- what is being changed
- why it is needed
- whether it is backward-compatible
- whether it belongs in v0.1 or a later version

---

## Repository structure

Contributors should generally work within these areas:

- `README.md` — human-readable overview
- `docs/one-page-spec.md` — concise summary specification
- `yaml/` — YAML model definition
- `schema json/` — machine-validated JSON Schema
- `sample json/` — example JSON instances
- `.github/workflows/validate-specs.yml` — validation workflow
- `CHANGELOG.md` — version history

If a contribution affects one layer, please check whether the corresponding layers should also be updated.

Example:
- If you change a field in the schema, you may also need to update:
  - sample JSON
  - README examples
  - one-page spec
  - changelog

---

## Naming conventions

Please follow these conventions where possible:

- Use descriptive, versioned filenames
- Keep version strings consistent across files
- Prefer stable naming over creative naming
- Avoid introducing multiple names for the same concept

Examples:

- `pseudo-structure-detection-v0.1.schema.json`
- `pseudo-structure-detection-v0.1.sample.json`
- `pseudo-structure-detection-v0.1.yaml`

---

## Pull request guidance

A good pull request should include:

- a clear title
- a short explanation of the change
- the reason for the change
- any affected files or components
- notes on compatibility, if relevant

Small, focused pull requests are preferred over large mixed changes.

---

## Commit message guidance

Recommended style:

- `docs: refine README wording`
- `schema: add required field validation`
- `examples: update sample JSON for v0.1`
- `ci: improve validation workflow`
- `spec: clarify pseudo-structure scoring rule`

This is not mandatory, but it helps keep the repository readable.

---

## Versioning expectations

Please do not silently introduce conceptual breaking changes.

Use the following rough distinction:

- **Patch-level change**: typo fixes, wording clarity, non-semantic cleanup
- **Minor-level change**: additive improvements that preserve current meaning
- **Breaking or model-defining change**: changes that alter detection logic, scoring meaning, field semantics, or interoperability assumptions

Breaking changes should be discussed explicitly and recorded in `CHANGELOG.md`.

---

## What to avoid

Please avoid:

- adding speculative features without structural rationale
- changing terminology inconsistently across files
- adding marketing-style language in place of definitions
- introducing schema complexity without practical validation benefit
- mixing future-version ideas into current-version files without clear labeling

---

## Discussion-first cases

Please open an issue or discussion first if your proposal involves:

- changing core detection dimensions
- changing score interpretation
- changing required output fields
- renaming major concepts
- introducing interoperability with external systems
- redefining what counts as “pseudo-structure”

These are model-level changes and should be handled deliberately.

---

## Validation expectation

Before submitting, ensure that sample files validate against the schema.

If CI is enabled, contributions are expected to pass the validation workflow.

---

## License

By contributing to this repository, you agree that your contributions will be provided under the same repository license unless explicitly stated otherwise.

---

## Final note

This repository is not only a document set.  
It is a **structured specification space**.

Please contribute in a way that strengthens:

- conceptual integrity
- validation reliability
- long-term readability
- structural precision
