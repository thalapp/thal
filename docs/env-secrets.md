# Environment config & secrets

Environment config and secret refs for thal. Secret values live in an
[arca](https://9aia.com/arca) vault — this repo carries `arca://` refs and
non-secret config only, never plaintext.

## Layout

| File | Env |
| --- | --- |
| `.env` | dev |
| `.env.preview` | preview |
| `.env.prod` | prod |

Each env file keeps non-secret values literal (model names, OAuth client
ids, flags) and marks secret slots with the `arca://` ref that backs them.
`arca.toml` declares the `[secrets]` surface — the env-var names `arca run`
is allowed to inject.

## Setup

```bash
arca init    # once per machine — creates the local age vault identity
```

## Use

```bash
arca run --env dev     -- <cmd>   # materialize dev secrets into the child env
arca run --env preview -- <cmd>
arca run --env prod    -- <cmd>

arca check --env prod            # validate config + vault + declared surface
arca list --env prod             # refs only — never values
```

Non-secret values are read from the env files as before; secrets arrive via
`arca run`'s injected environment.

## Updating a secret

Values never go on the command line — `arca put` reads stdin:

```bash
printf '%s' "$NEW_VALUE" | arca put arca://thal-env/<name> --env <env>

# e.g. rotate the dev stripe webhook secret after `stripe listen`:
printf '%s' "$whsec" | arca put arca://thal-env/stripe-endpoint-secret --env dev
```

## Notes

- `TARSI_GEMINI_API_KEY` and `DELPHIS_PASSWORD` are dev-only — pinned to
  `arca://dev/…` refs so they always resolve to the dev value.
- `APICLIENT_SESSION_COOKIE` is empty post-sign-in session state and is
  intentionally not vaulted. Set it locally, or
  `arca put arca://dev/thal-env/apiclient-session-cookie` and add it to
  `[secrets]` in `arca.toml`.
- `GCP_GOOGLE_CLIENT_ID`, `GEMINI_MODEL`, `RUNTIME_ENV`, `LAUNCH_EDITOR`,
  `DELPHIS_USER` are non-secret config — they stay literal in the env files.
- Secret values from before the arca migration remain in git history —
  rotate any that should no longer be considered live.
