# Tobi Flagship Use Case — AI-Agent Reasoning Gate

This repository is a narrow public Stage 1 use case for **AI Verification Engine / Tobi Validator**.

It demonstrates a validator-first PR gate around repository-owned `.tsubasa` artifacts.

## What this repo shows

This repo shows four things:

1. a valid Stage 1 `.tsubasa` artifact that passes `canon`
2. a drift-equivalent artifact that converges to the same canonical ASCII and the same `_h`
3. a malformed sibling that rejects deterministically
4. a GitHub Actions gate that blocks invalid artifact changes before merge

The point is not broad language coverage.
The point is a narrow, reproducible validator-backed gate.

## How it works

The repository carries three artifacts:

- `agent_artifacts/merge_token_valid.tsubasa`
- `agent_artifacts/merge_token_drift_equivalent.tsubasa`
- `agent_artifacts/merge_token_invalid.tsubasa`

The workflow does two jobs:

- **PR gate:** runs the public Tobi Validator GitHub Action against the valid artifact
- **Validation evidence:** downloads the released Stage 1 validator bundle, runs `canon` directly, checks canonical ASCII and `_h`, and confirms deterministic reject behavior for the malformed sibling

The gate contract is stored in:

- `policy/stage1_gate_contract.md`

The expected validator outputs are pinned in:

- `expected_outputs/`

## How to run

### GitHub Actions path

1. Create a repository secret:
    - `TOBI_EVAL_TOKEN`

2. Push this repository.

3. Open a pull request or run the workflow manually.

The PR gate uses:

```yaml
uses: OrganeticSphere/tobi-validator@v1