## what we expect and what worked before

Before 36.57.1 ​​​​or 36.57.0, ours packageRules sort PRs by environments based on the name of the second directory

- `**/discovery/helm-museum/description.yaml => groupName: discovery`
- `**/production/helm-museum/description.yaml => groupName: production`

## what we observe now

- `**/discovery/helm-museum/description.yaml => groupName: production`
- `**/production__/helm-museum/description.yaml => groupName: production`
