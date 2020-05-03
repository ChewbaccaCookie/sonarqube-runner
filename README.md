# SonarQube Runner - GitHub Action
<img src="https://www.sonarqube.org/assets/logo-31ad3115b1b4b120f3d1efd63e6b13ac9f1f89437f0cf6881cc4d8b5603a52b4.svg" width="320px">

Using this GitHub Action, scan your code with SonarQube scanner to detects bugs, vulnerabilities and code smells in more than 20 programming languages!
SonarQube is an open-source platform developed by SonarSource for continuous inspection of code quality to perform automatic reviews with static analysis of code to detect bugs, code smells, and security vulnerabilities on 20+ programming languages.

## Requirements

* You need a running SonarQube instance. [Instructions](https://docs.sonarqube.org/latest/setup/install-server/)

## Usage

The workflow, usually declared in `.github/workflows/build.yml`, looks like:

```yaml
on: push
name: Main Workflow
jobs:
  sonarQubeTrigger:
    name: SonarQube Trigger
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: SonarQube Scan
      uses: ChewbaccaCookie/sonarqube-runner@master
      with:
        host: ${{ secrets.SONARQUBE_HOST }}
        login: ${{ secrets.SONARQUBE_TOKEN }}
        projectKey: "<YOUR PROJECT KEY>"
```

You can change the analysis base directory by using the optional input `projectBaseDir` like this:

```yaml
uses:ChewbaccaCookie/sonarqube-runner@master
with:
  projectBaseDir: my-custom-directory
```

Container images built with this project include third party materials.
