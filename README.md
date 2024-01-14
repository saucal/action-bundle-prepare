# BUNDLE: Prepare

This action is a bundle of other actions which simplifies the workflow definition process for our standard wp-content rooted projects.

## Getting Started

This is the most common configuration for FTP deployments

```yml
- name: Prepare
  uses: saucal/action-bundle-prepare@v1
  with:
    slack-token: "${{ secrets.SLACK_BOT_TOKEN }}" # This should be preset as an organization level secret
    slack-channel: "XXXXXXXX"
    git-token: "${{ secrets.BOT_TOKEN }}"
```

If you're deploying to a WP VIP environment (GIT based) you'd do something like this

```yml
- name: Prepare
  uses: saucal/action-bundle-prepare@v1
  with:
    slack-token: "${{ secrets.SLACK_BOT_TOKEN }}" # This should be preset as an organization level secret
    slack-channel: "XXXXXXXX"
    git-token: "${{ secrets.BOT_TOKEN }}"
    repo: "wpcomvip/site-to-push"
    branch: "master"
```

## Full options

```yml
- uses: saucal/action-bundle-prepare@v1
  with:
    # Folder to clone the source on
    source: "source"

    # Folder to clone the built repo on
    built: "built"

    # Token to use throughout the process
    git-token: ""

    # Built repo name to.
    #
    # current-built is a special key you can use to use a repo within your organization, with the built prefix.
    repo: "current-built"

    # Branch to push the built state to (on the built repo)
    branch: "${{ github.ref_name }}"

    # Slack token to use when posting to Slack
    slack-token: ""

    # Slack channel to post to use when posting to Slack
    slack-channel: ""

    # Whether the repo is a full project or just a plugin or theme. When auto is provided, action evaluates this on its own.
    is-full-site: 'auto'

    # Whether our mu-plugins need to be added. When auto is provided, action evaluates this on its own.
    add-mu-plugins: 'auto'

    # In which directory to place our mu-plugins.
    mu-plugins-path: 'mu-plugins'

    # The branch to use for our mu-plugins.
    mu-plugins-branch: 'develop'

    # Whether to exclude or not outside collaborators from built repo.
    exclude-outside-collaborators: true
```
