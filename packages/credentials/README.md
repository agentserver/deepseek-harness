---
description: "Package map for the credential capability family: credential references, local storage, authorization flows, and pluggable browser authentication."
kind: "package-group"
---

# credentials/ — credentials and authorization

English | [中文](README.zh.md)

## Summary

The `credentials/` group lets configuration name secrets instead of embedding their values. Use `credentials/` to store, look up, and remove credentials, `credentials-local/` for private on-machine storage with per-run environment overrides, and `authorization/` when obtaining a credential requires asking a human. Browser authentication providers are maintained in the external [dsh-authentication repository](https://github.com/agentserver/dsh-authentication). Rotated stored values apply to the next model request, while `DEEPSEEK_API_KEY=… dsh` takes precedence for that run. Configuration files contain only credential names; local secret values remain readable only by the same OS user.

## Table of Contents

- [Packages](#packages)
- [Related documentation](#related-documentation)
- [Dev Note](#dev-note)

-----

<a id="packages"></a>
## Packages

The credential and browser-authentication capabilities are split into focused packages. Their READMEs cover day-to-day use; the subsystem reference owns the exhaustive contracts.

| Package | Role | ctx key |
|---|---|---|
| [`credentials/`](credentials/README.md) | Store, look up, and remove secrets at runtime while configuration only names them | `ctx.credentials` |
| [`credentials-local/`](credentials-local/README.md) | The default on-machine store: a private YAML file, environment overrides win | registers `ctx.credentials` |
| [`authorization/`](authorization/README.md) | Plugin-owned flows that obtain a credential by asking a human | `ctx.authorization` |

-----

<a id="related-documentation"></a>
## Related documentation

Start with the subsystem reference for the shared vocabulary, then the capability-seam table and the configuration surface of the local store.

- [Credentials subsystem reference](../../docs/subsystems/credentials.md) — `CredentialRef` and `CredentialKey`, per-operation resolution, UI-safe `CredentialInfo`, authorization flows, and the generated Cordis surface.
- [Capability seams](../../docs/capability-seams.md) — the Service Definition / Service Provider / Consumer split this family follows.
- [Generated configuration catalog](../../docs/config-catalog.md#deepseek-aidsh-credentials-local) — every accepted field of the local store.

<a id="dev-note"></a>
## Dev Note

<details>
<summary>Working context for maintainers — click to expand</summary>

None.

</details>
