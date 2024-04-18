<p align="center">
  <img alt="INSERT FAIAL TAG LINE" src="">
</p>

Verify your CUDA code with this github action.

![FTP test](https://github.com/cogumbreiro/setup-faial/workflows/FTP%20Test/badge.svg)
![FTPS test](https://github.com/cogumbreiro/setup-faial/workflows/FTPS%20Test/badge.svg)

---

# Setup Faial static analyzer

[Faial](https://gitlab.com/umb-svl/faial/) is a static analyzer for CUDA kernels
that can check for racy and data-race free kernels. This action downloads the
latest version of Faial and adds the executable `faial-drf` to the path.
**Action only supports `ubuntu-latest`.**

To learn more about Faial:
* [Project page](https://gitlab.com/umb-svl/faial/)
* [Tutorial](https://github.com/cogumbreiro/faial-tutorial)

# Usage

Use action `cogumbreiro/setup-faial`. You can optional set one parameter:

- `version`: the version represents the branch/tag/commit you wish to download
  from [Faial's repository](https://gitlab.com/umb-svl/faial/). The default
  is `main` which downloads the latest version.

# Tutorial

The repository [`cogumbreiro/faial-tutorial`](https://github.com/cogumbreiro/faial-tutorial)
serves as an example of using Faial as a GitHub Action. The
following is a minimal example of setting up Faial to check a file called `saxpy.cu` that is located in the root of the repository.

Create the file [`.github/workflows/run.yml`](https://github.com/cogumbreiro/faial-tutorial/blob/main/.github/workflows/run.yml) with the following code:

```yaml
on: [push]

jobs:
  check_drf:
    runs-on: ubuntu-latest
    name: Check that saxpy.cu is DRF.
    steps:
    - name: Check out code
      uses: actions/checkout@v1
    - name: Setup faial
      uses: cogumbreiro/setup-faial@v1.0
    - name: Check saxpy
      run: |
        faial-drf saxpy.cu
```


The key point is adding a step with `uses:
cogumbreiro/setup-faial@v1.0`, where the `name` can be any string you choose
(this string will appear in the GitHub Actions log as the title of the step).
```yaml
name: Setup faial
uses: cogumbreiro/setup-faial@v1.0
```

The following step runs `faial-drf saxpy.cu`, where `saxpy.cu` is the file we would like to check, which must be available in the repository:

```yaml
name: Check saxpy
run: |
  faial-drf saxpy.cu
```

# Acknowledgements

This action was based on Action
[`pavpanchekha/setup-z3`](https://github.com/pavpanchekha/setup-z3).
