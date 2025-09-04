<img src="https://wcm.io/images/favicon-16@2x.png"/> github-action-maven-build-sonar
======

Composite GitHub Action that verifies a Maven Build and analyzes the results in SonarCloud.

Usage example:

```yaml
# Build validation

name: Build

on:
  push:
    branches:
      - develop
  pull_request:
  workflow_dispatch:

jobs:
  build:

    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        java: [8, 11, 17]
        os: [ubuntu-latest]
        distribution: [temurin]

    steps:
      - name: Maven Build with SonarCloud
        uses: wcm-io-devops/github-action-maven-build-sonar@v1
        with:
          os: ${{ matrix.os }}
          java-version: ${{ matrix.java }}
          maven-executable: ./mvnw
          sonar-run-on-os: ubuntu-latest
          sonar-run-on-java-version: 21
          sonar-token: ${{ secrets.SONAR_TOKEN }}
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

For all parameters, see [action.yml](action.yml).
