# Maintenance verification — 18 October 2026

Source checkout: `9ca9a1aa6edc0955acbba2a7fb7f347fb7e770b3`.

## Executed checks

| Command | Observed result |
| --- | --- |
| `python scripts/check_repo.py` | No static errors: 51 Python, 9 shell, 10 JSON and 3 YAML files checked. 34 tests discovered: 32 passed, 2 skipped, 0 failures/errors |
| `python -m n64.run --input n64/fixtures/add.pseudo.c --dry-run` | Success; prompt/input hash emitted, no model loaded |
| `python -m n64.check --candidate n64/fixtures/add.reference.c` | Success; GCC host output matches all five reference cases |

The invalid-C diagnostic messages in the test log came from intentional rejection fixtures; their tests passed.

## Unverified scope

The two training-token tests were skipped because the real-tensor training dependencies were unavailable. Strict all-checks validation was not claimed. No checkpoint was loaded, no training or CUDA inference was run, and no exact tokenizer count was established. The fixture is synthetic; it is not output recovered from an N64 ROM. MIPS compilation and emulator/hardware execution remain untested.

These checks support the maintenance tooling and host harness. They do not establish model quality, N64 decompilation accuracy or release readiness.
