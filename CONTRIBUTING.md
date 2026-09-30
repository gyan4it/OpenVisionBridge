# Contributing to OpenVisionBridge

Thank you for contributing to **OpenVisionBridge**, a lightweight, modular, model-agnostic visual perception bridge.

## 1. Before Contributing

Read:

- `README.md`
- `VISION_BRIDGE_ARCHITECTURE.md`
- `LICENSE.md`
- `VIR_SCHEMA.json`
- `CODE_OF_CONDUCT.md`
- `SECURITY.md`

For major architectural, schema, API, licensing, or governance changes, open a design discussion before implementation.

## 2. Contribution Areas

Contributions are welcome in:

- image preprocessing
- OCR adapters
- geometry and shape detection
- region/object detection
- spatial reasoning
- visual graphs
- VIR schema and validation
- local SLM/LLM/VLM adapters
- question routing
- benchmarks and tests
- documentation
- performance and memory optimization
- security

## 3. Architecture Rules

Preserve this separation:

```text
Image
  -> Perception
  -> Visual Evidence
  -> VIR
  -> Visual Context
  -> AI Reasoning
```

Perception modules should not silently perform reasoning. Project-specific semantics should normally live in adapters rather than changing the core VIR unnecessarily.

## 4. Evidence Rules

Clearly distinguish:

- `DETECTED` — directly produced by a perception method.
- `DERIVED` — calculated from detected evidence.
- `INTERPRETED` — semantic interpretation requiring additional inference.
- `UNCERTAIN` — insufficiently reliable evidence.

Never convert uncertain evidence into a definitive claim merely to obtain an answer.

## 5. Confidence and Provenance

Inferred evidence should include a confidence value from `0.0` to `1.0` when technically possible.

Document what the score means. Do not describe an uncalibrated detector score as a calibrated probability.

Record provenance where practical:

```json
{
  "source_type": "GEOMETRY",
  "engine": "geometry_engine",
  "method": "polygon_detection"
}
```

## 6. VIR Changes

VIR is a public interoperability contract. Changes affecting required fields, types, semantics, confidence, provenance, or relationship vocabulary may be breaking changes.

Schema changes should include:

1. updated `VIR_SCHEMA.json`;
2. examples;
3. tests;
4. compatibility notes;
5. migration guidance when necessary.

## 7. New Adapters

Document:

```text
Purpose
Input
Output
Dependencies
Supported platforms
Resource requirements
Confidence behavior
Failure modes
License
Example usage
```

## 8. Dependencies

Before adding a dependency, consider:

- license compatibility;
- maintenance status;
- security;
- package size;
- memory/CPU/GPU requirements;
- offline operation;
- platform compatibility.

Avoid a heavy dependency when a substantially lighter solution is sufficient.

Third-party software remains subject to its own license.

## 9. AI Models

For model-based contributions, document:

- model and version;
- provider;
- model license;
- size;
- hardware requirements;
- network requirements;
- inference limitations.

Do not redistribute restricted model weights without permission.

## 10. Privacy

Do not introduce unnecessary image or visual-data uploads.

External services should be explicit, documented, and optional where practical.

Use synthetic or sanitized test images whenever possible.

## 11. Testing

Contributions should include appropriate:

- unit tests;
- integration tests;
- failure tests;
- regression tests.

Perception tests should cover valid, invalid, low-quality, ambiguous, and unsupported inputs.

VIR output should validate against the current schema.

## 12. Performance

Where relevant, report:

```text
latency
memory
CPU/GPU use
throughput
accuracy
```

Document the test environment and configuration.

## 13. Pull Requests

A pull request should explain:

- what changed;
- why it changed;
- implementation approach;
- tests performed;
- compatibility impact;
- dependency/license impact;
- security impact;
- performance impact.

Checklist:

- [ ] Architecture boundaries respected
- [ ] Tests added/updated
- [ ] Documentation updated
- [ ] VIR compatibility checked
- [ ] Confidence/provenance preserved
- [ ] Third-party licenses reviewed
- [ ] No secrets included
- [ ] Security considered
- [ ] No intentional visual fabrication

## 14. Commits

Prefer focused commits using:

```text
type(scope): short description
```

Examples:

```text
feat(ocr): add local OCR adapter
fix(vir): validate relationship references
docs(schema): explain confidence fields
test(spatial): add overlap cases
```

## 15. Contributions and Copyright

Contributors must have the right to submit their work.

Accepted contributors may be recognized in contributor records, release notes, documentation, or project acknowledgements.

Contributors retain rights in their original work to the extent provided by applicable law. By submitting a contribution, the contributor grants the project the permissions necessary to incorporate, maintain, modify, reproduce, and distribute that contribution under the project's applicable licensing framework.

## 16. Maintainer Review

The principal maintainer and designated maintainers may review contributions for correctness, architecture, security, licensing, performance, maintainability, documentation, and project scope.

A contribution may be accepted, revised, deferred, or declined.

## 17. Scope

A proposed feature should have a meaningful relationship to visual perception, visual representation, visual reasoning, visual interoperability, or supporting infrastructure.

## 18. Final Principle

```text
What the image contains
        ->
What the system detected
        ->
What the system derived
        ->
What the AI interprets
        ->
What the AI concludes
```

Contributions should make these boundaries clearer, not blur them.
