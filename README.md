# GitHub Action to show slack message with open PR

## Workflow

To use the GitHub Action in a given repository, simple add a workflow like

```yaml
on:
  schedule:
    - cron: "0 8 * * 1-5"
  workflow_dispatch:

name: Send Slack message with open PRs

jobs:
  slack-open-prs:
    name: Slack - open PRs
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: slack-open-prs
        uses: they-consulting/gh-action-open-pr-slack/.github/open-pr-slack-action@main
        with:
          slack-token: ${{ secrets.SLACK_TOKEN }}
          slack-channel: ###SLACK CHANNEL ID###
```

to the `.github/workflows/` folder in your repository.

Don't forget to set the inputs
- `slack-token`, with a new Secret in your Repository Settings
- `slack-channel` with the channel id available from Slack directly (Click on the Channel -> scroll to the Bottom -> Copy & Paste `Channel ID`)
