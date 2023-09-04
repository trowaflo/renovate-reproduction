## what we expect and what worked before

Before 36.57.1 ​​​​or 36.57.0, ours packageRules sort PRs by environments based on the name of the second directory

- `**/discovery/helm-museum/description.yaml => groupName: discovery`
- `**/production/helm-museum/description.yaml => groupName: production`

## what we observe now

- `**/discovery/helm-museum/description.yaml => groupName: production`
- `**/production__/helm-museum/description.yaml => groupName: production`

By doing so, I was able to target the problem to the `extends` list.

- When there is only `:semanticCommitScope(component-XXX)`, the 2 expected PRs are generated, one for each discovery and production.
- When there is only `:semanticCommitTypeAll(feat)`, only one PR is generated.
- When there are `:semanticCommitTypeAll(feat)` and `:semanticCommitScope(component-XXX)`, only the last rules are taken into account and only 1 PR is generated.
