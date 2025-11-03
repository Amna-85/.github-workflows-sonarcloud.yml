name: SonarCloud Analysis
on:
  push:
    branches: [main, master]
  pull_request:
    branches: [main, master]
jobs:
  sonarcloud:
    name: SonarCloud
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0
      - name: SonarCloud Scan
        uses: SonarSource/sonarcloud-github-action@v1.8
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
