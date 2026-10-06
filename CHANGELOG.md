# Changelog

## Unreleased

- Add Claude Opus 5.5, Sonnet 5.5, Opus 5, Sonnet 5, Opus 4.8, GPT-5.6
  Sol/Terra/Luna, and GLM-5 to the model catalog and US/EU region
  allowlists. Previously these were rejected by `resolveKiroModel` and
  filtered out of the model list.
- Point `pi.extensions` at `./src/extension.ts` so the package can be
  installed straight from git (`pi install git:github.com/...`) without
  a build step; `dist/` is gitignored.

## 0.1.3

- Drop `@mariozechner/pi-coding-agent` as a dependency and peer. pi-kiro
  used it only for the `ExtensionAPI` type; the minimal shape is now
  declared locally in `src/extension.ts`. Hosts on any pi version can
  install pi-kiro without a resolution error.
- Add `@mariozechner/pi-ai` `^0.72.1` as an explicit devDep (previously
  transitive via pi-coding-agent).
- `@mariozechner/pi-ai` stays declared as peer `*`.
- `ExtensionAPI` / `ProviderConfig` in the emitted `dist/extension.d.ts`
  are now local, not re-exported from pi-coding-agent. Consumers should
  keep importing these types from `@mariozechner/pi-coding-agent`
  directly; pi-kiro does not re-export them.
- Public API surface (`streamKiro`, `kiroModels`, `loginKiro`,
  `refreshKiroToken`, `resolveApiRegion`, `filterModelsByRegion`,
  `KiroCredentials`, `KiroModel`, etc.) is unchanged.
