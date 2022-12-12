
## Securing via github actions
[Github Actions](https://github.com/features/actions) is a CI platform builtin to Github that allows us to run CI pipeline upon changes of our code.<br>

We will add these Github actions:
* Secrets using [gitleaks](https://github.com/marketplace/actions/gitleaks)
* SAST using [Bandit](). 
* SCA
* IaC scanning using [Kics](https://github.com/marketplace/actions/kics-github-action).

Let's begin.<br>
Create this folder in your project's dir `.github/workflows`.<br>
All files should be generated under that folder.

### Gitleaks
Create a file called `gitleaks.yml` and copy this content.

```yml
name: gitleaks
on:
  pull_request:
  push:
    
jobs:
  scan:
    name: gitleaks
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0
      - uses: gitleaks/gitleaks-action@v2
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          GITLEAKS_LICENSE: ${{ secrets.GITLEAKS_LICENSE}} # Only required for Organizations, not personal accounts.
```

### SAST (Static application security testing)
Let's create this workflow `sast.yml`<br>
and copy this to the file:

```yml
name: Test SAST Bandit action PR comment

on:
  pull_request:
  push:

jobs:
  kics:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: mdegis/bandit-action@v1
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          path: "."
          level: high
          confidence: high
          exit_zero: true
```

### IaC Scaning With Kics

```yml

name: Test KICS action PR comment

on:
  pull_request:
  push:

jobs:
  kics:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: run kics Scan
      uses: checkmarx/kics-github-action@v1.6
      with:
        path: ./
        token: ${{ secrets.GITHUB_TOKEN }}
        output_path: myResults/
        ignore_on_exit: results
        enable_comments: true
```