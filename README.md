<p align="center"><img width="340" height="220" alt="MicorHs" src="https://github.com/user-attachments/assets/da0d8d9e-b823-4111-8fea-a2a81b6163bd" /></p>

# A GitHub Actions that installs MicroHs

This action provides `mcs`, `mcabal`, `cpphs`, and MicroHs compatible libraries.

It's also very fast (< 1s).

```yaml
# file .github/workflows/mhs.yml

name: MicroHs

concurrency:
  group: ${{ github.workflow }}-${{ github.head_ref || github.run_id }}
  cancel-in-progress: true

on:
  pull_request:
    branches:
      - main

jobs:
  build:
    strategy:
      fail-fast: false
      matrix:
        os:
          - ubuntu-latest
          - macos-latest
    runs-on: ${{ matrix.os }}
    steps:
      - uses: actions/checkout@v4
      - uses: sol/setup-MicroHs@nightly
      - run: mcabal -r build
```
