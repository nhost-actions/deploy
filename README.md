# nhost-deploy

Deploys an Nhost Project to app.nhost.io

## Usage

You can use this action after installing and authenticating the CLI to deploy an Nhost project:

```yaml
    - name: Install Nhost CLI
      id: install-nhost-cli
      uses: nhost-actions/install-nhost-cli@v1

    - name: Authenticate with Nhost
      uses: nhost-actions/authenticate@v1
      with:
        pat: ${{ secrets.NHOST_PAT }}

    - name: Deploy
      uses: nhost-actions/nhost-deploy@v1
      with:
        subdomain: ${{ env.SUBDOMAIN }}
```

You can also specify a git ref to deploy:

```yaml
    - name: Deploy
      uses: nhost-actions/nhost-deploy@v1
      with:
        subdomain: ${{ env.SUBDOMAIN }}
        git_ref: ${{ inputs.GIT_REF }}
```

## Inputs

| Name | Required | Default | Description |
|------|----------|---------|-------------|
| `subdomain` | yes | | Nhost subdomain |
| `git_ref` | no | `github.sha` or `github.ref` | Git ref to deploy |
| `message` | no | Commit message or event name | Deploy message |
| `user` | no | `github.actor` | User that triggered the deploy |
| `user_avatar_url` | no | `https://github.com/<actor>.png` | User avatar URL |
| `timeout` | no | `300` | Timeout in seconds |
