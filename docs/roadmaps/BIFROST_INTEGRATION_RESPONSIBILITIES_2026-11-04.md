# Kista: Optional Secrets Provider for Bifröst

**Date:** 2026-11-04  
**Repository:** `hrabanazviking/kista`  
**Implementation status:** Roadmap only; no application code modified.

## Relationship to the master roadmap

- **Canonical roadmap:** https://github.com/hrabanazviking/bifrost-viewer/blob/main/docs/roadmaps/BIFROST_SECOND_BRAIN_MASTER_EXPANSION_ROADMAP_2026-11-04.md
- **Local full copy:** [BIFROST_SECOND_BRAIN_MASTER_EXPANSION_ROADMAP_2026-11-04.md](BIFROST_SECOND_BRAIN_MASTER_EXPANSION_ROADMAP_2026-11-04.md)
- **Status:** Proposed work, not existing functionality. Confirm actual current installed state and protect existing data before writing code.
- **Ownership:** Bifröst Viewer coordinates the Second Brain. Skein and Skry own their APIs. Integrations must use documented, authenticated contracts and cannot assume direct PostgreSQL access.
- **Security:** Public Markdown only. No actual keys, OAuth client secrets, vault values, database passwords, user documents, personal account identifiers, logs, private state paths or private URLs.
- **Compatibility:** Preserve existing code behavior, published interfaces, licenses and attribution. Changes should be opt-in, reversible and regression-tested.

## Goal

Provide secrets to specific privileged provider workers without ever turning Kista into a searchable knowledge source or exposing its contents to agents.

## Repository-specific engineering responsibilities

1. Implement an opt-in, narrow Kista adapter to the Bifröst `SecretSource` interface; do not make Kista mandatory.
2. Support named capability resolution for OpenRouter and selected Google OAuth identities, not unrestricted `get all` secrets.
3. Use secure process-local IPC or controlled file descriptors; avoid secrets in command arguments, logs, serialized job payloads, provider error telemetry and prompts.
4. Expose health/locked/revoked/expired states without returning values.
5. Keep encrypted exports and vault recovery separate from ordinary document backups; never include vault keys in public or corpus artifacts.
6. Document how users supply **their own** credentials and OAuth configuration; never share the owner's credentials with others.
7. Add canary-value tests across runtime logs, retrieval, public Git trees and backup manifests.

## Engineering and security gates

- [ ] A read-only Bifröst AI key cannot request arbitrary Kista entries.
- [ ] Failed/locked Kista disables only relevant optional providers and leaves local Second Brain working.
- [ ] Canary secrets do not appear in Markdown, API output, retrieval results, logs or graphs.

## Delivery sequence

1. Read this repository's own architectural rules, domain boundaries and current source before editing.
2. Audit installed and unpublished development work; never assume a feature is absent simply because it is missing from the current public default branch.
3. Design a versioned optional integration through published API contracts; preserve baseline behavior.
4. Implement synthetic fixtures, unit tests, integration tests, timeouts and permission checks.
5. Test disconnection, false/stale results, recovery and security canaries.
6. Document capability level and deployment directions without secrets; require owner approval before live rollout.

**Canonical authority:** The primary Bifröst Viewer roadmap above resolves conflicts; individual source code and verified deployed evidence establish what is actually implemented.

