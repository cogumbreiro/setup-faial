<!-- <p align="center">
  <img alt="INSERT FAIAL TAG LINE" src="">
</p> -->

[Faial](https://gitlab.com/umb-svl/faial/) is a static analyzer for CUDA kernels that can check for racy and data-race free kernels. Analyze your CUDA kernel with this action!

![Faial install test](https://github.com/cogumbreiro/setup-faial/workflows/faial-install/badge.svg)

---
### Usage Example
Use action `cogumbreiro/setup-faial`. You can optional set one parameter:

- `version`: the version represents the branch/tag/commit you wish to download
  from [Faial's repository](https://gitlab.com/umb-svl/faial/). The default
  is `main` which downloads the latest version.

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
---

### Requirements
- Make sure your YAML file has this: ` runs-on: ubuntu-latest`
---

### Setup Steps
1. Select the repository you want to add the action to
2. Select the `Actions` tab
3. Select `Blank workflow file` or `Set up a workflow yourself`, if you don't see these options manually create a yaml file `Your_Project/.github/workflows/main.yml`
4. Paste the example above into your yaml file and save
5. Now you need to add a key to the `secrets` section in your project. To add a `secret` go to the `Settings` tab in your project then select `Secrets`. Add a new `Secret` for `password`
6. Update your yaml file settings
7. If you appreciate this github action give it a :star: or show off with one of the [badges below](#badge).
---

# Common Examples
This [`repo`](https://github.com/leloykun/flash-hyperbolic-attention-minimal/blob/main/.github/workflows/run.yml) has some good examples that might help you get started with Faial.


## Badge

If you appreciate this github action give it a :star: or show off with one of the badges below. Feel free to edit the text or color.

[<img alt="Faial Verified" src="https://img.shields.io/badge/Faial-Verified-%3CCOLOR%3E?style=for-the-badge&color=0077b6">](https://github.com/cogumbreiro/setup-faial)

```md
[<img alt="Faial Verified" src="https://img.shields.io/badge/Faial-Verified-%3CCOLOR%3E?style=for-the-badge&color=0077b6">](https://github.com/cogumbreiro/setup-faial)
```

[<img alt="Faial Verified" src="https://img.shields.io/badge/Faial-Verified-%3CCOLOR%3E?style=for-the-badge&color=2b9348">](https://github.com/cogumbreiro/setup-faial)

```md
[<img alt="Faial Verified" src="https://img.shields.io/badge/Faial-Verified-%3CCOLOR%3E?style=for-the-badge&color=2b9348">](https://github.com/cogumbreiro/setup-faial)
```

[<img alt="Faial Verified" src="https://img.shields.io/badge/Faial-Verified-%3CCOLOR%3E?style=for-the-badge&color=d00000">](https://github.com/cogumbreiro/setup-faial)

```md
[<img alt="Faial Verified" src="https://img.shields.io/badge/Faial-Verified-%3CCOLOR%3E?style=for-the-badge&color=d00000">](https://github.com/cogumbreiro/setup-faial)
```
---

<!-- ## Contributing to this project
Add guidelines for contribution -->

To learn more about Faial:
* [Project page](https://gitlab.com/umb-svl/faial/)
* [Tutorial](https://github.com/cogumbreiro/faial-tutorial)

# Acknowledgements

This action was based on Action
[`pavpanchekha/setup-z3`](https://github.com/pavpanchekha/setup-z3).   
The above readme was based on 
[`SamKirkland/FTP-Deploy-Action`](https://github.com/SamKirkland/FTP-Deploy-Action)