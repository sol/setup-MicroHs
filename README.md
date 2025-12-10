<p align="center"><img width="340" height="220" alt="MicorHs" src="https://github.com/user-attachments/assets/da0d8d9e-b823-4111-8fea-a2a81b6163bd" /></p>

# A GitHub Actions that installs MicroHs

This action provides `mcs`, `mcabal`, `cpphs`, and MicroHs compatible libraries.

It's also very fast (< 1s).

```yaml
# file .github/workflows/micro-hs.yml

name: MicroHs

on:
  pull_request:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: sol/setup-MicroHs@nightly
      - run: mcabal -r test
```
