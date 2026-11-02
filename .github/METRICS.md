# Profile metrics

The `Profile metrics` workflow generates three SVGs on `main`:

- `assets/metrics/overview.svg`: GitHub overview and full-year isometric calendar.
- `assets/metrics/development.svg`: languages and contributions to organization repositories.
- `assets/metrics/collaboration.svg`: user-created issues and pull requests, plus up to six compact achievements.

The workflow runs daily at 09:17 UTC (06:17 in São Paulo), on changes to its configuration, and manually from Actions. Generated-asset commits do not trigger another rendering run.

## Credentials

The workflow uses the repository-scoped GitHub Actions token for public-account data and generated-asset commits. No personal token is required by this tested configuration. This keeps organization repositories outside the installation's access out of the generated panels.

## Data scope

Languages include accessible owner, collaborator and organization-member repositories, with three public projects added explicitly. The indepth analyzer matches `vnschneider` and the public author aliases Vinícius Schneider, Vinicius Schneider and Schneider-AS and has a bounded analysis time. Results depend on accessible repositories, author matching and the time available for analysis; they are not an exhaustive audit of every contribution.

Notable contributions are filtered to organizations and include commits and pull requests. Follow-up displays issues and pull requests created by the user, including those outside this repository. WakaTime is not enabled and does not require an additional token.

## Dependencies

The Metrics revision is pinned to the stable `latest` commit resolved during setup:

`65836723097537a54cd8eb90f61839426b4266b6`

Review the stable action's input manifest when updating the revision. The snake workflow has its own concurrency group, generates light and dark SVGs, and publishes only to `output`.

Sources: [Metrics](https://github.com/lowlighter/metrics), [Languages](https://github.com/lowlighter/metrics/blob/latest/source/plugins/languages/README.md), [Snake](https://github.com/Platane/snk).

The recent-language section is disabled because the stable release crashed on a missing commit entry in GitHub activity events during the initial run. Most-used languages still use the bounded indepth analyzer.
