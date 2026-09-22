# dnsid Homebrew tap

The [DNSid](https://dnsid.ai) CLI — verifiable, domain-anchored identity for AI agents.

```sh
brew tap dnsid-ai/tap
brew install dnsid
```

Or in one command, without adding the tap:

```sh
brew install dnsid-ai/tap/dnsid
```

Then:

```sh
dnsid --version
dnsid            # command list
```

To upgrade, `brew upgrade`. To remove, `brew uninstall --cask dnsid`.

## Supported platforms

macOS (Apple Silicon and Intel) and Linux (amd64 and arm64).

Windows is not served by this tap — download the release archive from the
[installation docs](https://docs.dnsid.ai/cli-installation) instead.

## Publishing a new version

Actions → **Update cask** → Run workflow → enter the release version.

That is the whole process. The workflow fetches `SHA256SUMS` for that version,
checks every archive the cask references is actually downloadable, renders
`Casks/dnsid.rb`, and commits it. Tick **dry run** to see the result without
committing.

It fails without committing if the version has no artifacts behind it, so
running it against a tag whose release never uploaded anything is safe.

To render locally instead:

```sh
./scripts/render-cask.sh 2026.08.25-22f2882
```

## About this repository

`Casks/dnsid.rb` is generated. **Do not edit it by hand** — the next publish
overwrites it. Change `templates/dnsid.rb.tmpl` instead.

The download host is stated in exactly one place, `ARTIFACT_BASE` in
`scripts/render-cask.sh`. Changing where artifacts are served is a one-line
edit here and a re-run — the CLI's own repository holds no Homebrew
configuration and needs no credential for this tap.

The dnsid binary this tap installs is distributed under the terms in
[LICENSE](LICENSE).

Issues with the CLI itself belong on the upstream tracker, not here.
