## Overview

Warnings of GitHub Actions specification changes are recorded in annotations.  
Administrators need to check and fix annotations that contain GitHub Actions warnings,etc.  
With this script, you can easily get a list of annotations for jobs in the latest run of each workflow, by repository.

Example GitHub Actions specification change: [Deprecating save-state and set-output commands](https://github.blog/changelog/2022-10-11-github-actions-deprecating-save-state-and-set-output-commands/)

## Setup

### gh auth login

```bash
gh auth login
```

### Environment variable

<b>GITHUB_TOKEN</b>

## Usage

```bash
USAGE:
  gha_annotations [options] [arguments]

OPTIONS:
  -h|--help: help
  -l|--log-level: Filter annotations by log level (default: '^.*$')
  -d|--date: Run created date (default: 2022-10-01)

EXAMPLES:
  gha_annotations help
  gha_annotations $owner/$repo_name
  gha_annotations -l info $owner/$repo_name
  gha_annotations -d 2023-02-19 $owner/$repo_name
  gha_annotations -d 2022-02-19 -l "warning" $owner/$repo_name
```

<details close>
<summary><b>Example output</b></summary>
<br/>

```json
[
  {
    "workflow_id": "45347240",
    "workflow_name": "deploy_stg",
    "workflow_path": ".github/workflows/service-stg.yaml",
    "html_url": "https://github.com/exampleOrg/service/actions/runs/3909245279",
    "annotations": [
      {
        "annotation_level": "warning",
        "blob_href": "https://github.com/exampleOrg/service/blob/2e21ecc09e0e699c095062c956c6ee3e2994b95e/.github",
        "message": "Node.js 12 actions are deprecated. For more information see: https://github.blog/changelog/2022-09-22-github-actions-all-actions-will-begin-running-on-node16-instead-of-node12/. Please update the following actions to use Node.js 16: actions/checkout@v2, cue-lang/setup-cue@v1.0.0-alpha.2, docker/setup-buildx-action@v1, actions/cache@v2, aws-actions/configure-aws-credentials@v1, docker/build-push-action@v2"
      },
      {
        "annotation_level": "warning",
        "blob_href": "https://github.com/exampleOrg/service/blob/2e21ecc09e0e699c095062c956c6ee3e2994b95e/.github",
        "message": "The `save-state` command is deprecated and will be disabled soon. Please upgrade to using Environment Files. For more information see: https://github.blog/changelog/2022-10-11-github-actions-deprecating-save-state-and-set-output-commands/"
      },
      {
        "annotation_level": "warning",
        "blob_href": "https://github.com/exampleOrg/service/blob/2e21ecc09e0e699c095062c956c6ee3e2994b95e/.github",
        "message": "The `set-output` command is deprecated and will be disabled soon. Please upgrade to using Environment Files. For more information see: https://github.blog/changelog/2022-10-11-github-actions-deprecating-save-state-and-set-output-commands/"
      }
    ]
  },
  {
    // ry
  }
]
```

</details>

## LICENSE

[WTFPL license](./LICENSE)
