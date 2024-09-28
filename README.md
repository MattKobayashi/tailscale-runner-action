# Tailscale Runner Action
 A GitHub Action to start an ephemeral runner in a Docker container via Tailscale.

## Inputs

## `gh-app-id`

**Required** The app ID for your GitHub App.

## `gh-app-login`

**Required** The login name for your GitHub App.

## `gh-app-private-key`

**Required** The private key for your GitHub App.

## `runner-labels`

Labels to be added to the runner. Defaults to `linux,x64`.

## `runner-network`

The name of a custom Docker network to attach the runner to. Defaults to `bridge` (the default Docker bridge network).

## `runner-working-dir`

A path on the host for the runner working directory. Defaults to `/tmp/actions-runners`.

## `ssh-host`

**Required** The Tailscale hostname or Tailscale IP address of your Docker host.

## `ssh-known-hosts`

**Required** A list of entries to add to `~/.ssh/known_hosts`.

## `ssh-user`

**Required** The SSH username to use when logging into your Docker host.

## `ts-oauth-client-id`

**Required** Your Tailscale OAuth Client ID.

## `ts-oauth-secret`

**Required** Your Tailscale OAuth Client Secret.

## `ts-version`

The Tailscale client version to use. Defaults to `1.74.1`.
