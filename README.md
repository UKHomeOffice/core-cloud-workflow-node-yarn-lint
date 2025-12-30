# Core Cloud Workflow Node yarn lint

A GitHub Actions workflow for running yarn lint on Node.js projects to identify and report code quality issues.

## Overview

This workflow automates code linting of Node.js projects within the core-cloud ecosystem, ensuring code quality standards are met.

## Features

- Automated yarn lint scanning
- Code quality reporting

## Requirements

- Valid `package.json`, `package-lock.json` and valid `yarn run lint` command

## Usage

Reference this workflow in your GitHub Actions pipeline:

```yaml
jobs:
    lint:
        uses: UKHomeOffice/core-cloud-workflow-node-yarn-lint
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `working_directory` | Directory to run yarn lint in | No | `.` |
| `node_version` | Node version | No | `24` |


## Outputs

| Output | Description |
|--------|-------------|
| `yarn_lint_exit_code` | Exit code from yarn lint (0 = success) |

## Support

For issues or questions:
- Create an issue in this repository
- Contact the Sauron Team on Slack: #core-cloud-team-sauron
- For tag enforcement questions, contact the Checkov workflow maintainers: #core-cloud-team-sauron

---

## Updated Repository Structure
```
core-cloud-workflow-node-yarn-lint/
.github
├── workflows
|    └── self-test.yaml
|
├── action.yaml
├── CODEOWNERS
├── README.md
└── tests
    ├── test-lint-invalid/
    └── test-lint-valid/
```

### 📘 SonarQube Configuration 
– `sonar-project.properties`

```
sonar.exclusions=tests/**

```

This removes all test fixtures and example IaC from SonarQube analysis, ensuring the Quality Gate only evaluates the actual workflow, action code, and scripts.

| Directory           | Purpose                                               | Excluded From SAST? |
| ------------------- | ----------------------------------------------------- | ------------------- |
| `tests/**`          | Local yarn lint test harness (intentionally invalid code) | ✅ Yes               |
| `action.yaml`       | Composite action logic                                | ❌ No                |

This setup ensures clean SAST results without blocking PRs due to intentionally invalid IaC.

## Contributing

Please read [CONTRIBUTING.md](./CONTRIBUTING.md)

## Security

Please read [SECURITY.md](./SECURITY.md)