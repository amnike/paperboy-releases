# Paperboy — releases

Builds of Paperboy, and the version manifest the app reads.

**`version.json` is live.** The app fetches it on launch and every 30 minutes. Editing it
changes what every installed copy is allowed to do, within about half an hour.

| field | what it does |
|---|---|
| `min_version` | anything **below** this stops working and shows the update screen |
| `latest_version` | shown to the user; never enforced |
| `download_url` | where the update screen's button sends them |
| `grace_seconds` | how long a copy may run without reaching this file (259200 = 3 days) |

## Forcing everyone onto a new build

1. Bump `app/VERSION` in the source tree, build, and publish the new release here.
2. Change **both** `min_version` and `latest_version` to that number, and point
   `download_url` at the new asset.

Copies below `min_version` lock on their next check.

## Notes

- The app never downloads or installs anything itself — the button opens this page in a browser.
- First open on a new Mac shows an "unidentified developer" warning: right-click the app,
  then Open. That goes away once the build is signed with an Apple Developer ID.
