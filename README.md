# TMA Cloud Changelog

Release notes for TMA Cloud, served at <https://tma-cloud.github.io/changelog/> and shown on the
[wiki's changelog pages](https://tma-cloud.github.io/Wiki/docs/changelog/overview). The format
follows [Common Changelog](https://common-changelog.org), a stricter form of
[Keep a Changelog](https://keepachangelog.com).

## Files

- `index.json` lists every release, newest first, and names the `latest` one.
- `vX.Y.Z.json` holds one release. `schema.json` describes it.

## A Release

```json
{
  "version": "4.0.0",
  "tag": "v4.0.0",
  "date": "2026-10-20",
  "channel": "stable",
  "title": "Version 4.0.0 Changelog",
  "notice": "One sentence on what to do when upgrading.",
  "groups": {
    "changed": [{ "text": "Rename `NODE_ENV` to `APP_ENV`", "breaking": true }],
    "added": ["Add an About page to Settings"],
    "removed": ["Remove Google sign-in"],
    "fixed": ["Fix the Shared listing query"]
  }
}
```

- **`date`** is the release day in UTC+6, as `YYYY-MM-DD`. Use the same date in `index.json`.
- **`notice`** is optional: one sentence of upgrade guidance, such as a step users must take.
- **`groups`** are shown in this order: Changed, Added, Removed, Fixed. Leave out a group with
  nothing in it.
- **Breaking changes** are objects with `"breaking": true`. The wiki shows them first in their
  group, marked **Breaking:**.
- Releases before 4.0.0 use a flat `items` list. Do not use `items` for new releases.

## Writing an Entry

- Start with a verb in the imperative, as in a commit subject: "Add", "Fix", "Remove".
- Say what changed for the people using or running TMA Cloud, in one line that makes sense on its
  own. Merge commits that make one change into one entry.
- Leave out changes users never see: tests, CI, dev-only dependencies, and fixes to bugs that were
  never released.
- Mark anything that needs action when upgrading as breaking: a renamed or removed setting,
  endpoint or field, or a removed feature.
- Put names of settings, endpoints and commands in backticks; the wiki shows them as code.
- No filler such as "improved", "enhanced" or "better". Say what is different.

## Releasing

1. Add `vX.Y.Z.json` and validate it against `schema.json`.
2. Add the release at the top of `index.json`, and set `latest` and `updatedAt`.
3. Change the previous release's `intro`, if it has one, to "Previous stable release".
