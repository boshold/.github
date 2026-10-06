# .github

## Workflow templates

`workflow-templates/` shows up under Actions → New workflow in every org repository. Keep the CI
template's file name `ci.yml`: both release templates call `$/.github/workflows/ci.yml` with
`stage: release`. Templates pin `boshold/gh-actions-public` to the `v1.0.0` commit. The source of
truth is [`templates/`](https://github.com/boshold/gh-actions-public/tree/v1.0.0/templates) in
[boshold/gh-actions-public](https://github.com/boshold/gh-actions-public).
