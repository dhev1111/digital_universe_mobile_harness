# Universal Lab — Core-Preserving Blueprint (Draft 1)

## Non-negotiable product identity
Universal Lab is an interactive, game-like environment for developing and evolving a real AI Brain. The game presentation must never replace, fake, or weaken the underlying functionality. The Brain's original goal remains unchanged: research, reason, remember, learn from evidence, use specialist capabilities, create real software, evaluate results, and propose controlled self-improvement.

## Audit baseline: Digital Universe Lab v0.2 vs v0.3

### v0.2 — observed implementation
- Single-file HTML/CSS/JavaScript prototype; responsive, dark interface.
- Five organizational zones: Memory, Knowledge, Archive, Experiment, Toolbox.
- Add/edit/delete records; search and sorting; tags.
- Local persistence through IndexedDB with a localStorage fallback.
- JSON backup export/import with basic schema and field-size validation.
- Explicitly labels itself a local-first knowledge organizer, not a full AI.

### v0.3 — observed additions
- Keeps the v0.2 record-management experience.
- Adds a Knowledge Graph view for saved records and approved links.
- Adds a rule-based “Virtual Brain” that proposes record connections using shared tags and overlapping words.
- Shows proposal scores/reasons and requires the user to approve a link before it becomes an approved relationship.
- Stores approved links locally and includes them in backups.
- The graph visualization currently lays out at most 24 records, even if more records exist.

### What is real today
- Local record storage and retrieval in the browser.
- Rule-based similarity proposals; explicit human approval for relationships.
- A basic graph visualization and backup/import workflow.

### What is not implemented / not proven by these HTML files
- No actual AI model, LLM integration, internet research, or multi-model orchestration.
- No persistent semantic/episodic/procedural memory engine beyond user-entered records and simple links.
- No software-product build pipeline, code execution sandbox, automated test runner, evaluator, or rollback engine.
- No self-learning loop or autonomous module creation.
- No 50 GB quota manager, storage budgeting, or enforced hard-cap mechanism. Browser storage is controlled by the browser/device; localStorage fallback is especially limited.
- No native Android app or verified APK in these files.

## Core architecture direction

1. **Lab Shell / Game UI** — rooms, stations, inventory, recipes, progress, experiments, clear status indicators. UI is presentation only; it cannot grant permissions.
2. **Brain Core** — task understanding, planning, routing, state management, and result synthesis.
3. **Memory Engine** — working, episodic, semantic, procedural, associative/graph, and consolidation layers. Every stored item has provenance, timestamps, confidence, importance, and retention policy where applicable.
4. **Research & Model Connectors** — optional online research and external model adapters when connected/configured; offline mode remains useful with local data and available tools. Never pretend internet/model access exists when it does not.
5. **Capability/Ingredient Registry** — versioned modules with explicit interfaces, dependencies, permissions, resource needs, test requirements, and compatibility metadata.
6. **Creation Factory** — turns a product specification plus selected capabilities into a plan, generated files/code, and a candidate artifact.
7. **Sandbox & Test Chamber** — isolated build/test execution with resource limits, captured logs, reproducible test results, and no automatic production activation.
8. **Evaluation & Learning** — compares outcomes to acceptance criteria, records evidence, diagnoses failures, and proposes changes; it must distinguish measured results from guesses.
9. **Safety / Permission Kernel** — deterministic checks outside model output; deny-by-default for sensitive actions; approval gates for installing modules, network actions, destructive changes, and activation.
10. **Versioning / Rollback** — immutable baseline, candidate versions, change manifests, checksums, and recovery path.
11. **Storage Governor** — hard configured cap of 50 GB across managed app storage; check capacity before writes, reserve emergency space, deduplicate, compact, archive, and reject/defer writes safely if quota would be exceeded. Never claim the cap applies to storage outside the app's control.
12. **Audit Log** — records actions, evidence, approvals, test results, failures, and rollbacks without silently deleting critical security evidence.

## Game-like product creation loop

`Goal → choose recipe/capabilities → resolve dependencies → build candidate → test → evaluate → human approval (where required) → activate → monitor → rollback if needed`

“Ingredients” are real modules/tools/configuration and their dependencies, not decorative icons. Unlocks/progress are awarded only for real, verifiable capabilities and test results. A visual success animation must not imply a build or test passed when it did not.

## Initial milestone sequence

- **M0 — Preserve & baseline:** keep v0.2/v0.3 originals unchanged; document their behavior and limitations.
- **M1 — Core contract:** define data schemas, capability interface, permission boundary, event/audit model, and testable acceptance criteria.
- **M2 — Playable Lab shell:** mobile-first room/station UI and module inventory backed by real state, not fake progress.
- **M3 — Memory foundation:** local structured store, graph relationships, deduplication, import/export, migrations, integrity checks.
- **M4 — Storage governor:** configurable 50 GB ceiling, budget accounting, pre-write checks, safe quota behavior, cleanup policy and tests.
- **M5 — Capability assembly:** recipe/dependency resolver and versioned module registry.
- **M6 — Creation & testing:** candidate workspace, build/test adapter, logs, result reports, failure handling.
- **M7 — Learning proposals:** evidence-based evaluation and human-approved candidate changes with rollback.
- **M8 — Optional online intelligence:** model/research adapters with explicit configuration, privacy controls, and honest offline fallback.
- **M9 — Android packaging:** only after core workflows are tested; retain local-first operation.

## Acceptance rules
- The original Brain purpose must remain visible in product requirements and regression tests.
- Every visible capability must map to a real implementation or be clearly labeled “planned / simulated”.
- No model can directly override the permission kernel.
- New or modified modules run as candidates until required tests pass and required approval is given.
- Failed activation must have a tested rollback path.
- Storage writes that would breach the configured cap must be blocked/deferred safely; do not delete critical evidence to make room.
- Preserve existing versions and user data; no destructive rewrite or remote push without explicit instruction.

## Audit note
This is a source-level review of the two supplied standalone HTML files. It is not a runtime/browser test and does not prove that behavior works on the user's particular phone. Before implementation, test the original files on-device and preserve backups.
