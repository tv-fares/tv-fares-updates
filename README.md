# TV Fares Glass — Updates

Public distribution channel for signed TV Fares Glass Android TV APK releases. **The application source code remains in the separate private repository** `tv-fares/tv-fares`.

## Status
The update channel is **not active yet**. No trusted release APK or `latest.json` has been published. Do not use test APKs from GitHub Actions as automatic updates.

## Release requirements
1. Configure one durable Android APK signing key securely in private CI secrets. Never commit the keystore or passwords to this repository.
2. Confirm the signing identity and package ID of the installed app. An APK signed by a different certificate cannot update an installed version in place; do not uninstall the existing version until migration is planned.
3. Build a signed APK for `sa.personal.oootv.glass`, verify its package ID, monotonic `versionCode`, signing certificate, and SHA-256 checksum.
4. Upload the verified APK as a public GitHub Release asset.
5. Only after step 4 publish `latest.json` at the repository root, with this format:

```json
{
  "packageName": "sa.personal.oootv.glass",
  "versionCode": 13,
  "versionName": "1.3",
  "apkUrl": "https://github.com/tv-fares/tv-fares-updates/releases/download/v1.3/tv-fares-glass-v1.3.apk",
  "sha256": "<the real APK SHA-256 hash>"
}
```

The JSON above is **an example, not a live release manifest**. Only use matching values from the actually published signed APK.

6. Set the app's update feed to `https://raw.githubusercontent.com/tv-fares/tv-fares-updates/main/latest.json` before building the first trusted version.

Android TV asks the user to approve installations; automatic discovery/download does not imply silent installation. Test the update path on the actual Xiaomi TV Stick before publishing it as working.
