# Environment config & secrets

Environment config and secret refs for thal. Secret values live in an
[cuora](https://9aia.com/cuora) vault — this repo carries `cuora://` refs and
non-secret config only, never plaintext.

## Layout

| File | Env |
| --- | --- |
| `.env` | dev |
| `.env.preview` | preview |
| `.env.prod` | prod |

Each env file keeps non-secret values literal (model names, OAuth client
ids, flags) and marks secret slots with the `cuora://` ref that backs them.
`cuora.toml` declares the `[secrets]` surface — the env-var names `cuora run`
is allowed to inject.

## Setup

```bash
cuora init    # once per machine — creates the local age vault identity
```

## Use

```bash
cuora run --env dev     -- <cmd>   # materialize dev secrets into the child env
cuora run --env preview -- <cmd>
cuora run --env prod    -- <cmd>

cuora check --env prod            # validate config + vault + declared surface
cuora list --env prod             # refs only — never values
```

Non-secret values are read from the env files as before; secrets arrive via
`cuora run`'s injected environment.

## Updating a secret

Values never go on the command line — `cuora put` reads stdin:

```bash
printf '%s' "$NEW_VALUE" | cuora put cuora://thal/<name> --env <env>

# e.g. rotate the dev stripe webhook secret after `stripe listen`:
printf '%s' "$whsec" | cuora put cuora://thal/stripe-endpoint-secret --env dev
```

## Notes

- `TARSI_GEMINI_API_KEY` and `DELPHIS_PASSWORD` are dev-only — pinned to
  `cuora://dev/…` refs so they always resolve to the dev value.
- `APICLIENT_SESSION_COOKIE` is empty post-sign-in session state and is
  intentionally not vaulted. Set it locally, or
  `cuora put cuora://dev/thal/apiclient-session-cookie` and add it to
  `[secrets]` in `cuora.toml`.
- `GCP_GOOGLE_CLIENT_ID`, `GEMINI_MODEL`, `RUNTIME_ENV`, `LAUNCH_EDITOR`,
  `DELPHIS_USER` are non-secret config — they stay literal in the env files.
- Secret values from before the cuora migration remain in git history —
  rotate any that should no longer be considered live.
