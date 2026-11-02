# Profile metrics

The `Profile metrics` workflow generates three SVGs on `main`:

- `assets/metrics/overview.svg`: GitHub overview and full-year isometric calendar.
- `assets/metrics/development.svg`: languages and contributions to organization repositories.
- `assets/metrics/collaboration.svg`: user-created issues and pull requests, plus up to six compact achievements.

The workflow runs daily at 09:17 UTC (06:17 in São Paulo), on changes to its configuration, and manually from Actions. Generated-asset commits do not trigger another rendering run.

## Credentials

METRICS_TOKEN is the user-provided account token for Metrics queries. The repository-scoped github.token is used separately for generated-asset commits. METRICS_EXCLUDED_REPOS holds the list of private repositories excluded during setup; names are kept in an Actions secret, not in the public configuration. Refresh that exclusion list when repository visibility changes. Repository names are disabled in notable-contribution badges as an additional display constraint.

## Data scope

Languages estimate the language distribution of accessible repositories the user contributes to, using the default API-based analyzer. The indepth commit analyzer is disabled because it made the initial rendering unnecessarily slow. The chart describes repositories, not an individual skill level or an exact count of the user's code.

Notable contributions are filtered to organizations and include commits and pull requests; repository-name labels are disabled. Follow-up displays issues and pull requests created by the user, including those outside this repository. WakaTime is not enabled and does not require an additional token.

## Dependencies

The Metrics revision is pinned to the stable `latest` commit resolved during setup:

`65836723097537a54cd8eb90f61839426b4266b6`

Review the stable action's input manifest when updating the revision. The snake workflow has its own concurrency group, generates light and dark SVGs, and publishes only to `output`.

Sources: [Metrics](https://github.com/lowlighter/metrics), [Languages](https://github.com/lowlighter/metrics/blob/latest/source/plugins/languages/README.md), [Snake](https://github.com/Platane/snk).

The recent-language section is disabled because the stable release crashed on a missing commit entry in GitHub activity events during the initial run. Most-used languages use the default API-based analyzer.
