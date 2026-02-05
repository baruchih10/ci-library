# CI Library Repo (Reusable Workflows)

This repo is intended to be published as a separate repository, so other repos can reuse its workflows.

## What to do (class setup)

1. Create a repo named `ci-library`
2. Upload/push the contents of this folder
3. Create a tag `v1` (or a release) so app repos can reference a stable version:
   - `git tag v1`
   - `git push --tags`

Then in an app repo you can call:

```yaml
jobs:
  build:
    uses: ORG_OR_USER/ci-library/.github/workflows/docker-build.yml@v1
    with:
      image_name: flask-demo
      docker_context: .
    secrets: inherit
```

## Notes
- This example pushes to GHCR using the caller repo name in the tag
- Requires in the **calling repo**:
  - Actions workflow permissions: Read & write
  - packages: write permission in workflow
