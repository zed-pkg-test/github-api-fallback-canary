# github-api-fallback-canary

Public, non-secret package used to verify Zed's production fallback chain.

The `Live Zed GitHub and Cloudflare E2E` workflow builds exact commits of
`zed-pkg/zed-cli` and `zed-pkg-test/zed-pkg-e2e`, then:

1. runs the real `zed publish` command with the registry intentionally
   unreachable;
2. requires the package artifact and metadata sidecar to be hosted on this
   repository's GitHub Release;
3. compares direct GitHub bytes with the `cdn.zpkg.net/github/...` proxy;
4. verifies `registry.zpkg.net` reconstructs version metadata from the public
   sidecar; and
5. runs normal and frozen installs with registry and R2 access disabled so the
   CLI must consume the GitHub Release directly.

Everything in this repository and its Releases is public. Never add credentials,
private source, customer data, or user data to the canary payload.
