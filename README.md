# K8S Workload Guard

Offline policy checker for Kubernetes Pod and Deployment JSON resources.

## Quick start

Requires Python 3.10+; standard library only. Run from this repository's root.

```bash
python -m app.cli examples/workloads.json
```

## Tests

```bash
python -m unittest discover -s tests -v
```

## Architecture

- `app/`: CLI and core analysis logic.
- `examples/`: safe, synthetic example inputs.
- `tests/`: repeatable unit tests.
- `.github/workflows/tests.yml`: CI tests on push and pull requests.

## Engineering decisions

- Read-only analysis: the tool does not modify its input files.
- Machine-readable JSON output facilitates automation and regression testing.
- No third-party dependencies; quick to run and review.

## Current scope and limitations

Accepts Pod or apps/v1 Deployment resource documents in JSON. Checks a limited set of good-practice safeguards (resource limits, non-root settings, image tags). Does not parse YAML or guarantee a Kubernetes workload is secure. Each issue names its resource and container.

## Good Claude Code evaluation tasks

1. Ask Claude Code to inspect the implementation and report specific risks without making changes.
2. Add one regression test for a realistic edge case, then request a minimal fix.
3. Review its diff, run the test suite, check failure behavior, and document what you accepted or rejected.

## Attribution

This repository was initially created with AI assistance. Describe subsequent changes and test results accurately when presenting it as a portfolio project.

## License

MIT. See [LICENSE](LICENSE).
