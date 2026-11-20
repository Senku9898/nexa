# Nexa — Distribution

This repository holds:

- GitHub Releases for verified signed APKs
- Version manifest source of truth
- Release process documentation

## Important rules

- Never commit APK binaries into the repository history.
- Only attach signed, verified production APKs to GitHub Releases.
- Do not expose signing keys, passwords, or private configuration.

## URLs

| Resource | URL |
|----------|-----|
| Website | https://senku9898.github.io |
| Profile pattern | https://senku9898.github.io/u/{PROFILE_ID} |
| Releases | https://github.com/Senku9898/nexa/releases |
| Latest APK | https://github.com/Senku9898/nexa/releases/latest/download/nexa.apk |
| Version manifest | https://senku9898.github.io/version.json |

## Publishing a verified release (manual)

1. Build & sign the production APK offline.
2. Compute SHA-256:
   ```bash
   sha256sum nexa.apk
   ```
3. Create a new GitHub Release with tag `vX.Y.Z`.
4. Upload the APK as asset named `nexa.apk`.
5. Update `version.json` (in the Pages repo) with real values.
6. Verify the direct download link works.

## version.json schema

```json
{
  "versionName": "1.0.0",
  "versionCode": 1,
  "minimumSupportedVersionCode": 1,
  "apkUrl": "https://github.com/Senku9898/nexa/releases/download/v1.0.0/nexa.apk",
  "sha256": "the-sha256-hex",
  "releaseNotes": "First public release",
  "publishedAt": "2026-11-20T00:00:00Z"
}
```

## Future automation

A safe workflow template is in `.github/workflows/release.yml`.  
It must never publish unverified builds automatically and must not expose signing secrets in logs.
