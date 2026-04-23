# Stage 1 Gate Contract

This repository demonstrates a narrow Stage 1 validator-first gate.

Gate surface:
- `agent_artifacts/merge_token_valid.tsubasa` must pass `canon`
- `agent_artifacts/merge_token_drift_equivalent.tsubasa` must converge to the same canonical ASCII and the same `_h`
- `agent_artifacts/merge_token_invalid.tsubasa` must reject with a deterministic malformed-numeric diagnostic

This contract is repository-owned and reviewable.
It is intentionally narrow.
It does not imply runtime, backend, or API behavior.