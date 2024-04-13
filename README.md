# Setup Faial static analyzer

[Faial](https://gitlab.com/umb-svl/faial/) is a static analyzer for CUDA kernels
that can check for racy and data-race free kernels. This action downloads the
latest version of `faial` and adds the executable `faial-drf` to the path.
**Action only supports `ubuntu-latest`.**

# Usage

Use action `cogumbreiro/setup-faial`. You can optional set one parameter:

- `version`: the version represents the branch/tag/commit you wish to download
  from [Faial's repository](https://gitlab.com/umb-svl/faial/). The default
  is `main` which downloads the latest version.

# Acknowledgements

This action was based on Action
[`pavpanchekha/setup-z3`](https://github.com/pavpanchekha/setup-z3).
