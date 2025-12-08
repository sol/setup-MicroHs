# A GitHub Actions to install MicroHs

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
      - run: mcabal -r install nanospec
```
