# Tailscale Runner Action
 A GitHub Action to start an ephemeral runner in a Docker container via Tailscale.

## How to use

You'll need the following things:

- A Tailscale tailnet containing one or more machines running the Docker daemon, and an [OAuth client](https://tailscale.com/kb/1215/oauth-clients#setting-up-an-oauth-client).
- [Tailscale SSH](https://tailscale.com/kb/1193/tailscale-ssh) needs to be enabled on the tailnet, with [appropriate `accept` ACLs](https://tailscale.com/kb/1193/tailscale-ssh#action) configured. `accept` must be used for SSH ACLs, `check` is **not** supported. Tailscale ephemeral nodes are automatically tagged with the value from `ts-tag`, this tag can be used with ACLs.
- A [GitHub App](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/authenticating-to-the-github-api#authenticating-arc-with-a-github-app) for authenticating ephemeral runners.

## Example workflow

At a minimum, your workflow should look like this:

```
jobs:
  create-runner:
    name: Create self-hosted Actions runner
    runs-on: ubuntu-latest
    steps:
      - name: Create self-hosted Actions runner
        uses: MattKobayashi/tailscale-runner-action@v1.0.2
        with:
          gh-app-id: ${{ secrets.GH_APP_ID }}
          gh-app-login: MattKobayashi
          gh-app-private-key: ${{ secrets.GH_APP_PRIVATE_KEY }}
          ssh-host: 192.0.2.1
          ssh-known-hosts: ${{ secrets.SSH_KNOWN_HOSTS }}
          ssh-user: matthew
          ts-oauth-client-id: ${{ secrets.TS_OAUTH_CLIENT_ID }}
          ts-oauth-secret: ${{ secrets.TS_OAUTH_SECRET }}
```

Ephemeral runners will remove themselves after completing a single job in a workflow. If you need multiple jobs processed, a matrix can be used to spawn multiple runners:

```
jobs:
  create-runner:
    name: Create self-hosted Actions runner
    runs-on: ubuntu-latest
    strategy:
      fail-fast: false
      matrix:
        runner-name: [
          runner1,
          runner2,
          runner3
        ]
    steps:
      - name: Create self-hosted Actions runner
        uses: MattKobayashi/tailscale-runner-action@v1.0.2
        with:
          gh-app-id: ${{ secrets.GH_APP_ID }}
          gh-app-login: MattKobayashi
          gh-app-private-key: ${{ secrets.GH_APP_PRIVATE_KEY }}
          ssh-host: 192.0.2.1
          ssh-known-hosts: ${{ secrets.SSH_KNOWN_HOSTS }}
          ssh-user: matthew
          ts-oauth-client-id: ${{ secrets.TS_OAUTH_CLIENT_ID }}
          ts-oauth-secret: ${{ secrets.TS_OAUTH_SECRET }}
```

## Considerations

- A working directory for each runner is created in the location specified by `runner-working-dir`, by default this is set to `/tmp/actions-runners`. If you're processing many jobs, this directory can grow quite large. It's recommended to create a cronjob on the host to regularly clean up this directory. `/tmp` is also cleared when the host is rebooted.
- Runners created by this action are capable of executing `docker run` actions, i.e. for CI testing of images. Test containers should be executed with the `--rm` flag and stopped at the end of the workflow using `docker container stop` to avoid zombie containers being left running on the host. Images should also be removed using `docker image rm` to avoid filling the host's disk with cached images. An example of how to achieve this can be seen below:

	```
		  # Build and export image to Docker daemon
	      # https://github.com/docker/build-push-action
	      - name: Build and export to Docker
	        uses: docker/build-push-action@v6.8.0
	        with:
	          load: true
	          tags: "${{ env.REPO_NAME }}/${{ env.IMAGE_NAME }}:test"
	      # Install uuid-runtime package
	      - name: Install `uuid-runtime`
	        run: |
	          set -x
	          apt-get --yes install uuid-runtime
	      # Test the built image
	      - name: Test image
	        run: |
	          set -x
	          CONTAINER_ID="$(uuidgen)"
	          docker container run --attach=stdout --attach=stderr --init --name=$CONTAINER_ID --rm ${{ env.REPO_NAME }}/${{ env.IMAGE_NAME }}:test &
	          sleep 60
	          docker container stop $CONTAINER_ID
	      # Remove the test image
	      - name: Remove test image
	        if: ${{ !cancelled() }}
	        run: |
	          set -x
	          docker image rm --force ${{ env.REPO_NAME }}/${{ env.IMAGE_NAME }}:test
	```

## Inputs

### `gh-app-id`

**Required** The app ID for your GitHub App.

### `gh-app-login`

**Required** The login name for your GitHub App.

### `gh-app-private-key`

**Required** The private key for your GitHub App.

### `runner-labels`

Labels to be added to the runner. Defaults to `linux,x64`.

### `runner-network`

The name of a custom Docker network to attach the runner to. Defaults to `bridge` (the default Docker bridge network).

### `runner-working-dir`

A path on the host for the runner working directory. Defaults to `/tmp/actions-runners`.

### `ssh-host`

**Required** The Tailscale hostname or Tailscale IP address of your Docker host.

### `ssh-known-hosts`

**Required** A list of entries to add to `~/.ssh/known_hosts`.

### `ssh-user`

**Required** The SSH username to use when logging into your Docker host.

### `ts-oauth-client-id`

**Required** Your Tailscale OAuth Client ID.

### `ts-oauth-secret`

**Required** Your Tailscale OAuth Client Secret.

### `ts-tag`

A unique tag to apply to ephemeral Tailscale nodes. Defaults to `github-actions`.

### `ts-version`

The Tailscale client version to use. Defaults to `1.74.1`.
