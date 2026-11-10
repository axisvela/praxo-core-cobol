# PRAXO-CORE for COBOL

Dedicated repository for the COBOL implementation of PRAXO-CORE: an
embeddable, MIT-licensed agent execution kernel with policy controls,
human-in-the-loop approval, checkpoints, events, and tool calling.

- Package: `praxo-core-cobol` (`0.4.0`)
- Registry: Source
- Install: `Source build (see README)`
- Documentation: https://axisvela.github.io/praxo-core/languages/cobol/
- Mirror repository: https://github.com/axisvela/praxo-core-cobol
- Canonical source: https://github.com/axisvela/praxo-core/tree/main/language/cobol
- Release index: https://axisvela.github.io/praxo-core/languages/registry-status/

This repository is a discovery mirror of the canonical COBOL source.
The monorepo remains the source of truth and the release workflow source. Shared
conformance vectors are included under `spec/`, so the implementation can be
built and tested here.

## Verify

Build and test instructions are in `language/cobol/README.md`. The
monorepo CI runs the language's conformance, API snapshot, and native tests.

PRAXO-CORE is not a hosted model, workflow engine, identity provider, or safety
controller. Do not infer exactly-once execution, complete sandbox isolation,
production security certification, live-provider behavior, or physical safety
from this package.

MIT licensed.
