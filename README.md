# hitokoto-content

Remote content pack for the 今日のひとこと app (see `Document/Development_plan.md`
section 6–7 in the app repo).

- `main` branch: production. Apps built with the prod flavor read
  `https://raw.githubusercontent.com/huchu90/hitokoto-content/main/`.
- `dev` branch: testing. Dev builds read `.../dev/`.

## Releasing new content

1. Edit the JSON files (schema: plan section 6).
2. Bump `contentVersion` in `manifest.json` (must be higher than the version
   in use, or apps ignore the pack).
3. Validate in the app repo: copy the JSON files into its `assets/data/`
   and run `dart run tool/validate_content.dart` (it also checks that every
   illustration file exists; remote packs never carry images).
4. Push to `dev`, check on a dev build, then merge to `main`.

Apps check at most every 12 hours and use a new pack from the next cold start.
