# MergeRay review workflow

A small reusable GitHub Actions workflow that runs the
[MergeRay](https://www.mergeray.com) Action for same-repository pull requests.

Call it from a repository that has been enrolled with the MergeRay service,
pinning this repository by **full commit SHA**:

```yaml
name: MergeRay
on:
  pull_request:
    branches: [main]
permissions: {}
jobs:
  mergeray:
    permissions:
      id-token: write
      contents: read
      actions: read
      pull-requests: read
      checks: write
    uses: Mergeray/review-workflow/.github/workflows/mergeray-review.yml@FULL_COMMIT_SHA
```

The MergeRay service only accepts runs of the exact workflow commit that was
registered for your repository. Installing or calling this workflow does not by
itself grant access: enrollment and authorization are required.
