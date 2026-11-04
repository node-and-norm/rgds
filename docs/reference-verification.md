# Reference verification: Regulated Gate Decision Support

Run the existing checks in a disposable checkout. The [workflow](../.github/workflows/validate.yml) uses Python 3.11. The [dependency file](../requirements.txt) allows a range of `jsonschema` versions, so capture the installed versions with the result.

## Environment and exact commands

Use Git, a POSIX shell, Python 3.11 and internet access for cloning and dependency installation. The source declares the CI version without a separate supported-minimum statement. [Workflow](../.github/workflows/validate.yml).

```sh
(
  set -eu
  review_dir="$(mktemp -d)"
  git clone https://github.com/node-and-norm/rgds.git "$review_dir/repository"
  cd "$review_dir/repository"
  git checkout --detach 40224993db145f16a160f811da194b9e64999050
  git rev-parse HEAD
  python3.11 --version
  python3.11 -m venv .venv
  . .venv/bin/activate
  python -m pip install -r requirements.txt
  export PYTHONDONTWRITEBYTECODE=1
  python scripts/validate_all_examples.py --strict
  python -m unittest discover -s tests -v
  git diff --exit-code
  git status --short
  python -m pip freeze
)
```

The first check should print six `[PASS]` records and end with `All example decision logs conform to schema and semantic invariants.` The regression suite contains nine tests and should end with `OK`. Strict mode makes warnings fail the example check. [Batch validator](../scripts/validate_all_examples.py), [tests](../tests/test_validation.py).

## Inspect one record

Inside the same disposable environment, run:

```sh
python scripts/validate_decision_log.py   decision-log/decision-log.schema.json   examples/rgds-dec-0006-ai-assisted-conditional-go.json   --strict
```

The command should return exit status 0. The validator returns 1 for a failed rule and 2 for a configuration or read error. `--strict` enables semantic checks and treats warnings as failures. [Single-record validator](../scripts/validate_decision_log.py).

## Write effects and interpretation

Installation writes the disposable environment. Python may create cache files. Regression tests write derived records inside temporary directories and preserve the canonical examples. [Test implementation](../tests/test_validation.py).

Record the source commit, operating system, Python and dependency versions, exact command and exit status. A pass establishes the tested structural and semantic conditions. Actual review, correct decisions and institutional effectiveness require separate evidence. [Requirements traceability](../evaluation/requirements-traceability-matrix.md), [prospective evaluation](../evaluation/evaluation-plan.md).
